<template>
    <div ref="dom"></div>
</template>

<script>
import echarts from 'echarts'
import { on, off } from '@/libs/tools'

var _this;

export default {
  name: 'serviceRequests',
  data () {
    return {
      dom: null,
      scatterData: null,
      cellSize: [80, 80],
      pieRadius: 30

    }
  },

  methods: {
    resize () {
      this.dom.resize()
    },

    getVirtulData() {
        var date = +echarts.number.parseDate('2017-02-01');
        var end = +echarts.number.parseDate('2017-03-01');
        var dayTime = 3600 * 24 * 1000;
        var data = [];
        for (var time = date; time < end; time += dayTime) {
            data.push([
                echarts.format.formatTime('yyyy-MM-dd', time),
                Math.floor(Math.random() * 10000)
            ]);
        }
        return data;
    },

    getPieSeries(scatterData, chart) {
        return echarts.util.map(scatterData, function (item, index) {
            var center = chart.convertToPixel('calendar', item);
            return {
                id: index + 'pie',
                type: 'pie',
                center: center,
                label: {
                    normal: {
                        formatter: '{c}',
                        position: 'inside'
                    }
                },
                radius: _this.pieRadius,
                data: [
                    {name: '工作', value: Math.round(Math.random() * 24)},
                    {name: '娱乐', value: Math.round(Math.random() * 24)},
                    {name: '睡觉', value: Math.round(Math.random() * 24)}
                ]
            };
        });
    },

    getPieSeriesUpdate(scatterData, chart) {
        return echarts.util.map(this.scatterData, function (item, index) {
            var center = chart.convertToPixel('calendar', item);
            return {
                id: index + 'pie',
                center: center
            };
        });
    },

  },
  mounted () {

    var option = {
      tooltip : {},
          legend: {
              data: ['工作', '娱乐', '睡觉'],
              bottom: 20
          },
          calendar: {
              top: 'middle',
              left: 'center',
              orient: 'vertical',
              cellSize: this.cellSize,
              yearLabel: {
                  show: false,
                  textStyle: {
                      fontSize: 30
                  }
              },
              dayLabel: {
                  margin: 20,
                  firstDay: 1,
                  nameMap: ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六']
              },
              monthLabel: {
                  show: false
              },
              range: ['2017-02']
          },
          series: [{
              id: 'label',
              type: 'scatter',
              coordinateSystem: 'calendar',
              symbolSize: 1,
              label: {
                  normal: {
                      show: true,
                      formatter: function (params) {
                          return echarts.format.formatTime('dd', params.value[0]);
                      },
                      offset: [-this.cellSize[0] / 2 + 10, -this.cellSize[1] / 2 + 10],
                      textStyle: {
                          color: '#000',
                          fontSize: 14
                      }
                  }
              },
              data: this.scatterData
          }]
    }

    this.$nextTick(() => {
      _this = this;

      this.scatterData = this.getVirtulData();

      this.dom = echarts.init(this.$refs.dom)
      this.dom.setOption(option)

      console.log(this.dom)

      if (!app.inNode) {
          var pieInitialized;
          setTimeout(function () {
              pieInitialized = true;
              _this.dom.setOption({
                  series: _this.getPieSeries(_this.scatterData, _this.dom)
              });
          }, 10);

          app.onresize = function () {
              if (pieInitialized) {
                  _this.dom.setOption({
                      series: _this.getPieSeriesUpdate(_this.scatterData, _this.dom)
                  });
              }
          };
      }

      on(window, 'resize', this.resize)
    })
  },

  beforeDestroy () {
    off(window, 'resize', this.resize)
  }
}
</script>
