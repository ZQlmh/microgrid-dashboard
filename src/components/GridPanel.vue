<template>
  <div ref="chartRef" class="w-full h-full"></div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
import * as echarts from 'echarts'

const chartRef = ref<HTMLElement | null>(null)
let myChart: echarts.ECharts | null = null

const initChart = () => {
  if (chartRef.value) {
    myChart = echarts.init(chartRef.value, 'dark')
    const option = {
      backgroundColor: 'transparent',
      tooltip: { trigger: 'axis' },
      legend: { 
        data: ['充电桩功率', '光伏实际发电功率', '其他负荷功率', '储能充放电功率', '并网点预计功率', '并网点实际功率'],
        bottom: 0, 
        icon: 'circle',
        itemWidth: 8,
        textStyle: { color: '#a3a3a3', fontSize: 10 }
      },
      grid: { left: '4%', right: '4%', bottom: '15%', top: '15%', containLabel: true },
      xAxis: {
        type: 'category',
        boundaryGap: false,
        data: ['0', '2', '4', '6', '8', '10', '12', '14', '16', '18', '20', '22', '24'],
        axisLine: { lineStyle: { color: 'rgba(255, 255, 255, 0.1)' } },
        axisLabel: { color: '#a3a3a3', fontSize: 10 }
      },
      yAxis: {
        type: 'value',
        name: '功率/kW',
        nameTextStyle: { color: '#a3a3a3', fontSize: 10, align: 'right' },
        splitLine: { lineStyle: { color: 'rgba(255, 255, 255, 0.05)', type: 'dashed' } },
        axisLabel: { color: '#a3a3a3', fontSize: 10 }
      },
      series: [
        {
          name: '并网点实际功率', type: 'line', smooth: true, symbolSize: 8,
          data: [1500, 800, -1000, -2500, -1800, 500, 1800, -1000, 500, 1500, 500, 1000, -800],
          itemStyle: { color: '#00d2ff' },
          areaStyle: { color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{ offset: 0, color: 'rgba(0, 210, 255, 0.3)' }, { offset: 1, color: 'transparent' }]) }
        },
        {
          name: '并网点预计功率', type: 'line', smooth: true, symbolSize: 6,
          data: [1200, 500, -800, -2000, -1500, 800, 1500, -800, 800, 1200, 800, 1200, -500],
          itemStyle: { color: '#e2e8f0' },
          lineStyle: { type: 'dashed' }
        },
        {
          name: '光伏实际发电功率', type: 'line', smooth: true, symbolSize: 8,
          data: [0, 0, 0, -2800, -3000, -1000, 0, 0, 0, 0, 0, 0, 0],
          itemStyle: { color: '#c084fc' },
          areaStyle: { color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{ offset: 0, color: 'rgba(192, 132, 252, 0.3)' }, { offset: 1, color: 'transparent' }]) }
        },
        {
          name: '储能充放电功率', type: 'line', smooth: true, symbolSize: 8,
          data: [2000, 1500, 800, -500, -800, -1500, -2000, -1500, -800, 500, 1500, 2000, 1500],
          itemStyle: { color: '#fb923c' }
        }
      ]
    }
    myChart.setOption(option)
    window.addEventListener('resize', () => myChart?.resize())
  }
}

onMounted(() => initChart())
onUnmounted(() => window.removeEventListener('resize', () => myChart?.resize()))
</script>