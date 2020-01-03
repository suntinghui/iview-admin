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
          text: ''
        },
        tooltip: {
          trigger: 'axis'
        },
        legend: {
          data: ['M', 'D', 'A', 'B']
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
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
        xAxis: {
          type: 'category',
          boundaryGap: false,
          data: ['周一', '周二', '周三', '周四', '周五', '周六', '周日']
        },
        yAxis: {
          type: 'value'
        },
        series: [{
            name: 'M',
            type: 'line',
            stack: '总量',
            data: [120, 132, 101, 134, 90, 230, 210]
          },
          {
            name: 'D',
            type: 'line',
            stack: '总量',
            data: [220, 182, 191, 234, 290, 330, 310]
          },
          {
            name: 'A',
            type: 'line',
            stack: '总量',
            data: [150, 232, 201, 154, 190, 330, 410]
          },
          {
            name: 'B',
            type: 'line',
            stack: '总量',
            data: [320, 332, 301, 334, 390, 330, 320]
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
