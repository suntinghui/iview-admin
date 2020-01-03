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
          left: 'center'
        },
        tooltip: {
          trigger: 'item',
          formatter: '{a} <br/>{b} : {c} ({d}%)'
        },
        legend: {
          orient: 'vertical',
          left: 'left',
          data: ['在网数据', '新入网数据', '退网数据', '退服数据']
        },
        series: [{
          name: '设备运营指标',
          type: 'pie',
          radius: '55%',
          center: ['50%', '60%'],
          data: [{
              value: 335,
              name: '在网数据'
            },
            {
              value: 110,
              name: '新入网数据'
            },
            {
              value: 90,
              name: '退网数据'
            },
            {
              value: 35,
              name: '退服数据'
            }
          ],
          emphasis: {
            itemStyle: {
              shadowBlur: 10,
              shadowOffsetX: 0,
              shadowColor: 'rgba(0, 0, 0, 0.5)'
            }
          }
        }]
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
