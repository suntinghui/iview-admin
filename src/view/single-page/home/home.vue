<template>
  <div>
    <Row :gutter="20">
      <i-col :xs="24" :md="16" :lg="8" style="height: 120px;padding-bottom: 10px;">
        <infor-card shadow color="#2d8cf0" icon="ios-trending-up" icon-size="36">
          <div class="count-to-con">
            <count-to :end="982" class="count-text">
              <span slot="right" class="slot-text">&nbsp;&nbsp;当日收入</span>
            </count-to>
          </div>

          <div class="count-to-con">
            <count-to :end="278641" class="slot-text">
              <span slot="right" class="slot-text">&nbsp;&nbsp;历史收入</span>
            </count-to>
          </div>
        </infor-card>
      </i-col>

      <i-col :xs="24" :md="16" :lg="8" style="height: 120px;padding-bottom: 10px;">
        <infor-card shadow color="#ed3f14" icon="ios-exit-outline" icon-size="36">
          <div class="count-to-con">
            <count-to :end="14" class="count-text">
              <span slot="right" class="slot-text">&nbsp;&nbsp;当日收入</span>
            </count-to>
          </div>

          <div class="count-to-con">
            <count-to :end="2975" class="slot-text">
              <span slot="right" class="slot-text">&nbsp;&nbsp;历史收入</span>
            </count-to>
          </div>
        </infor-card>
      </i-col>

      <i-col :xs="24" :md="16" :lg="8" style="height: 120px;padding-bottom: 10px;">
        <infor-card shadow color="#ff9900" icon="ios-contract" icon-size="36">
          <div class="count-to-con">
            <count-to :end="714" class="count-text">
              <span slot="right" class="slot-text">&nbsp;&nbsp;新入网数</span>
            </count-to>
          </div>

          <div class="count-to-con">
            <count-to :end="62975" class="slot-text">
              <span slot="right" class="slot-text">&nbsp;&nbsp;在线总数</span>
            </count-to>
          </div>
        </infor-card>
      </i-col>
    </Row>

    <Row :gutter="20" style="margin-top: 10px;">
      <i-col :md="24" :lg="12" style="margin-bottom: 20px;">
        <Card shadow>
          <zhou style="height: 350px;" />
        </Card>
      </i-col>
      <i-col :md="24" :lg="12" style="margin-bottom: 20px;">
        <Card shadow>
          <luye style="height: 350px;" />
        </Card>
      </i-col>
    </Row>

    <Row :gutter="20" style="margin-top: 10px; display: none;">
      <i-col :md="24" :lg="12" style="margin-bottom: 20px;">
        <Card shadow>
          <yao style="height: 500px;" />
        </Card>
      </i-col>
      <i-col :md="24" :lg="12" style="margin-bottom: 20px;">
        <Card shadow>
          <luye style="height: 500px;" />
        </Card>
      </i-col>
    </Row>


    <Row :gutter="20" style="margin-top: 10px;">
      <i-col :md="24" :lg="12" style="margin-bottom: 20px;">
        <Card shadow>
          <chen style="height: 350px;" />
        </Card>
      </i-col>
      <i-col :md="24" :lg="12" style="margin-bottom: 20px;">
        <Card shadow>
          <mei style="height: 350px;" />
        </Card>
      </i-col>
    </Row>

  </div>
</template>

<script>
  import InforCard from '_c/info-card'
  import CountTo from '_c/count-to'
  import {
    ChartPie,
    ChartBar
  } from '_c/charts'
  import Zhou from './zhou.vue'
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
      Zhou,
      Yao,
      Luye,
      Chen,
      Mei
    },
    data() {
      return {

      }
    },
    mounted() {
      //
    }
  }
</script>

<style lang="less">
  .countto-page-row {
    height: 200px;
  }

  .count-to-con {
    display: block;
    width: 100%;
    text-align: center;
  }

  .count-text {
    font-size: 40px;
    color: #000C17;
  }

  .slot-text {
    font-size: 16px;
    color: #666666;
  }

  .unit-class {
    font-size: 30px;
    color: #2D8CF0;
  }
</style>
