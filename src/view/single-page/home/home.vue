<template>
  <div>
    <Row :gutter="20">
      <i-col :xs="18" :md="12" :lg="6" v-for="(infor, i) in inforCardData" :key="`infor-${i}`" style="height: 120px;padding-bottom: 10px;">
        <infor-card shadow :color="infor.color" :icon="infor.icon" :icon-size="36">
          <count-to :end="infor.count" count-class="count-style"/>
          <p>{{ infor.title }}</p>
        </infor-card>
      </i-col>
    </Row>

    <Row :gutter="20" style="margin-top: 10px;">
      <i-col :md="24" :lg="12" style="margin-bottom: 20px;">
        <Card shadow>
          <chart-pie style="height: 300px;" :value="pieData" text="设备运营指标"></chart-pie>
        </Card>
      </i-col>
      <i-col :md="24" :lg="12" style="margin-bottom: 20px;">
        <Card shadow>
          <chart-bar style="height: 300px;" :value="barData" text="每周用户活跃量"/>
        </Card>
      </i-col>
    </Row>

    <Row :gutter="20" style="margin-top: 10px;">
      <i-col :md="24" :lg="12" style="margin-bottom: 20px;">
        <Card shadow>
          <yao style="height: 500px;"/>
        </Card>
      </i-col>
      <i-col :md="24" :lg="12" style="margin-bottom: 20px;">
        <Card shadow>
          <luye style="height: 500px;"/>
        </Card>
      </i-col>
    </Row>


    <Row :gutter="20" style="margin-top: 10px;">
      <i-col :md="24" :lg="12" style="margin-bottom: 20px;">
        <Card shadow>
          <chen style="height: 420px;"/>
        </Card>
      </i-col>
      <i-col :md="24" :lg="12" style="margin-bottom: 20px;">
        <Card shadow>
          <mei style="height: 420px;"/>
        </Card>
      </i-col>
    </Row>

  </div>
</template>

<script>
import InforCard from '_c/info-card'
import CountTo from '_c/count-to'
import { ChartPie, ChartBar } from '_c/charts'
import Yao from './yao.vue'
import Luye from './luye.vue'
import Chen from './chen.vue'
import Mei from './mei.vue'

export default {
  name: 'home',
  components: {
    InforCard,
    CountTo,
    ChartPie,
    ChartBar,
    Yao,
    Luye,
    Chen,
    Mei
  },
  data () {
    return {
      inforCardData: [
        { title: '当日收入(万)', icon: 'ios-trending-up', count: 203, color: '#2d8cf0' },
        { title: '当日支出(万)', icon: 'ios-exit-outline', count: 3.9, color: '#19be6b' },
        { title: '历史收入(万)', icon: 'ios-contract', count: 1242, color: '#ff9900' },
        { title: '历史支出(万)', icon: 'ios-share-outline', count: 67, color: '#ed3f14' }
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
