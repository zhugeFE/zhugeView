<template>
  <div>
    <demo-panel subtitle="重置x轴">
      <zg-charts :store="store" :showList="showList" type="bar" seriesName="点击次数。。。" reverseXAxis></zg-charts>
    </demo-panel>
  </div>
</template>

<script>
  import json from './json/eventList'
  import ZgCharts from '../../../../src/components/echarts/charts'

  export default {
    components: {ZgCharts},
    name: 'reverse',
    data () {
      return {
        showList: ['pv', '官网-进入官网', 'web-进入首页', 'click', '登录-进入登录页', '官网-首页-依场景而设', '登录', '注册-进入注册界面', 'Demo-进入demo', '看板-进入模块'],
        store: json.app_data
      }
    }
  }
</script>

<style lang="sass">

</style>
