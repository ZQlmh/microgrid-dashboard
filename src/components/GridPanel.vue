<template>
  <div ref="chartRef" class="chart-container"></div>
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
      legend: { data: ['购电功率', '售电功率'], top: 10, right: 10, textStyle: { color: '#e2e8f0' } },
      grid: { left: '3%', right: '4%', bottom: '3%', containLabel: true },
      xAxis: {
        type: 'category',
        boundaryGap: false,
        data: ['00:00', '04:00', '08:00', '12:00', '16:00', '20:00', '24:00'],
        axisLine: { lineStyle: { color: '#1e3a8a' } }
      },
      yAxis: {
        type: 'value',
        name: '功率 (kW)',
        splitLine: { lineStyle: { color: 'rgba(255, 255, 255, 0.1)' } },
        axisLine: { lineStyle: { color: '#e2e8f0' } }
      },
      series: [
        {
          name: '购电功率', type: 'line', smooth: true,
          data: [120, 132, 101, 134, 90, 230, 210],
          itemStyle: { color: '#ef4444' },
          areaStyle: { color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{ offset: 0, color: 'rgba(239, 68, 68, 0.8)' }, { offset: 1, color: 'rgba(239, 68, 68, 0.1)' }]) }
        },
        {
          name: '售电功率', type: 'line', smooth: true,
          data: [20, 12, 191, 234, 290, 30, 10],
          itemStyle: { color: '#10b981' },
          areaStyle: { color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{ offset: 0, color: 'rgba(16, 185, 129, 0.8)' }, { offset: 1, color: 'rgba(16, 185, 129, 0.1)' }]) }
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