<template>
  <div>
    <Row :gutter="20">
      <i-col :xs="12" :md="8" :lg="4" v-for="(infor, i) in inforCardData" :key="`infor-${i}`" style="height: 120px;padding-bottom: 10px;">
        <infor-card shadow :color="infor.color" :icon="infor.icon" :icon-size="36">
          <count-to :end="infor.count" count-class="count-style"/>
          <p>{{ infor.title }}</p>
        </infor-card>
      </i-col>
    </Row>
    <Row :gutter="20" style="margin-top: 10px;">
      <i-col :md="24" :lg="8" style="margin-bottom: 20px;">
        <Card shadow>
          <chart-pie style="height: 300px;" :value="pieData" text="设备运营指标"></chart-pie>
        </Card>
      </i-col>
      <i-col :md="24" :lg="16" style="margin-bottom: 20px;">
        <Card shadow>
          <chart-bar style="height: 300px;" :value="barData" text="每周用户活跃量"/>
        </Card>
      </i-col>
    </Row>
    <Row>
      <Card shadow>
        <example style="height: 310px;"/>
      </Card>
    </Row>
    <Row>
      <Card shadow>
        <tableyao style="height: 520px;"/>
      </Card>
    </Row>
  </div>
</template>

<script>
import InforCard from '_c/info-card'
import CountTo from '_c/count-to'
import { ChartPie, ChartBar } from '_c/charts'
import Example from './example.vue'
import Tableyao from './tableyao.vue'
export default {
  name: 'home',
  components: {
    InforCard,
    CountTo,
    ChartPie,
    ChartBar,
    Example,
    Tableyao
  },
  data () {
    return {
      inforCardData: [
        { title: '当日收入(万)', icon: 'ios-trending-up', count: 203, color: '#2d8cf0' },
        { title: '当日支出(万)', icon: 'ios-exit-outline', count: 3.9, color: '#19be6b' },
        { title: '历史收入(万)', icon: 'ios-contract', count: 1242, color: '#ff9900' },
        { title: '历史支出(万)', icon: 'ios-share-outline', count: 67, color: '#ed3f14' },
        { title: '设备在网数(千)', icon: 'ios-git-network', count: 102, color: '#E46CBB' },
        { title: '在仓票数(万)', icon: 'ios-ribbon-outline', count: 140, color: '#9A66E4' }
      ],
      pieData: [
        { value: 335, name: '在网设备' },
        { value: 76, name: '新入网设备' },
        { value: 20, name: '退网设备' },
        { value: 13, name: '退服设备' }
      ],
      barData: {
        Mon: 13253,
        Tue: 34235,
        Wed: 26321,
        Thu: 12340,
        Fri: 24643,
        Sat: 1322,
        Sun: 1324
      }
    }
  },
  mounted () {
    //
  }
}
</script>

<style lang="less">
.count-style{
  font-size: 50px;
}
</style>
