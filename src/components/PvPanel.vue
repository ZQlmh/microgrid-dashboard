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
        data: ['充电功率', '放电功率'],
        top: 0, right: 0, icon: 'circle',
        itemWidth: 8, textStyle: { color: '#a3a3a3', fontSize: 10 }
      },
      grid: { left: '0%', right: '0%', bottom: '5%', top: '30%', containLabel: true },
      xAxis: {
        type: 'category', boundaryGap: false,
        data: ['0', '2', '4', '6', '8', '10', '12', '14', '16', '18', '20', '22'],
        axisLine: { lineStyle: { color: 'rgba(255, 255, 255, 0.1)' } },
        axisLabel: { color: '#a3a3a3', fontSize: 9 }
      },
      yAxis: {
        type: 'value',
        name: '充放电趋势',
        nameTextStyle: { color: '#a3a3a3', fontSize: 9, padding: [0, 0, 0, 20] },
        splitLine: { show: false },
        axisLabel: { show: false },
        min: -20000, max: 20000
      },
      series: [
        {
          name: '充电功率', type: 'line', smooth: true, symbol: 'none',
          data: [15000, 16000, 15000, 8000, 5000, 1000, 0, 0, 12000, 14000, 16000, 15000],
          itemStyle: { color: '#00d2ff' }
        },
        {
          name: '放电功率', type: 'line', smooth: true, symbol: 'none',
          data: [0, 0, 0, 0, 0, -2000, -18000, -18000, -16000, -2000, 0, 0],
          itemStyle: { color: '#ffb13b' }
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