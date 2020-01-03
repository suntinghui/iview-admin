<template>
  <div ref="dom"></div>
</template>

<script>
  import echarts from 'echarts'
  import {
    on,
    off
  } from '@/libs/tools'
  export default {
    name: 'serviceRequests',
    data() {
      return {
        dom: null
      }
    },
    methods: {
      resize() {
        this.dom.resize()
      }
    },
    mounted() {
      const option = {
        title: {
          text: '',
        },
        tooltip: {
          trigger: 'axis'
        },
        legend: {
          data: ['在仓票数量', '库存票数量']
        },
        toolbox: {
          show: true,
          feature: {
            dataView: {
              show: true,
              readOnly: false
            },
            magicType: {
              show: true,
              type: ['line', 'bar']
            },
            restore: {
              show: true
            },
            saveAsImage: {
              show: true
            }
          }
        },
        calculable: true,
        xAxis: [{
          type: 'category',
          data: ['1月', '2月', '3月', '4月', '5月', '6月', '7月', '8月', '9月', '10月', '11月', '12月']
        }],
        yAxis: [{
          type: 'value'
        }],
        series: [{
            name: '在仓票数量',
            type: 'bar',
            data: [52.0, 24.9, 57.0, 63.2, 25.6, 76.7, 35.6, 62.2, 32.6, 90.0, 66.4, 33.3],
            markPoint: {
              data: [{
                  type: 'max',
                  name: '最大值'
                },
                {
                  type: 'min',
                  name: '最小值'
                }
              ]
            },
            markLine: {
              data: [{
                type: 'average',
                name: '平均值'
              }]
            }
          },
          {
            name: '库存票数量',
            type: 'bar',
            data: [12.6, 25.9, 39.0, 26.4, 28.7, 70.7, 75.6, 82.2, 48.7, 18.8, 46.0, 42.3],
            markPoint: {
              data: [{
                  name: '年最高',
                  value: 182.2,
                  xAxis: 7,
                  yAxis: 183
                },
                {
                  name: '年最低',
                  value: 2.3,
                  xAxis: 11,
                  yAxis: 3
                }
              ]
            },
            markLine: {
              data: [{
                type: 'average',
                name: '平均值'
              }]
            }
          }
        ]
      }
      this.$nextTick(() => {
        this.dom = echarts.init(this.$refs.dom)
        this.dom.setOption(option)
        on(window, 'resize', this.resize)
      })
    },
    beforeDestroy() {
      off(window, 'resize', this.resize)
    }
  }
</script>
