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
      dom: null
    }
  },
  methods: {
    resize () {
      this.dom.resize()
    }
  },
  mounted () {
    const option = {
          tooltip: {
              formatter: '{a} <br/>{b} : {c}%'
          },
          toolbox: {
              feature: {
                  restore: {},
                  saveAsImage: {}
              }
          },
          series: [
              {
                  name: '业务指标',
                  type: 'gauge',
                  detail: {formatter: '{value}%'},
                  data: [{value: 50, name: '完成率'}]
              }
          ]
    }
    this.$nextTick(() => {
      _this = this;
      
      this.dom = echarts.init(this.$refs.dom)
      this.dom.setOption(option)
      on(window, 'resize', this.resize)

	  setInterval(function () {
	      option.series[0].data[0].value = (Math.random() * 100).toFixed(2) - 0;
	      _this.dom.setOption(option, true);
	  },2000);

    })
  },
  beforeDestroy () {
    off(window, 'resize', this.resize)
  }
}
</script>
