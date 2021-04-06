<template>
  <div id="mycharts" ref="myRef" class="chart-box" />
</template>
<script lang="js">
import { defineComponent, getCurrentInstance, ref, onMounted } from 'vue';
export default defineComponent({
  name: 'echarts',
  setup() {
    const { ctx } = getCurrentInstance();
    const myRef = ref(null);

    const initT = () => {
      const myChart = ctx.echarts.init(document.getElementById('mycharts'));
      console.log(myChart);
      myChart.setOption({
        title: {
          text: '本月数据统计'
        },
        tooltip: {},
        legend: {
          data: ['任务数量']
        },
        xAxis: {
          data: ['javascript', 'vue', 'ts', 'react', 'nginx']
        },
        yAxis: {},
        series: [
          {
            name: '任务数量',
            type: 'bar',
            data: [5, 20, 36, 10, 10]
          }
        ]
      });
    };

    onMounted(() => {
      initT();
    });
    return {
      myRef
    };
  }
});
</script>

<style lang="css" scoped>


img{
  width: 400px;
  height: 400px;
  background: red;
}
.chart-box{
  width: 600px;
  height: 600px;
}
</style>
