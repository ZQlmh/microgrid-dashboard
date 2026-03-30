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
      tooltip: { trigger: 'axis', axisPointer: { type: 'shadow' } },
      legend: {
        data: ['调节方向', '实际值', '调节目标'],
        top: 0, left: 'center', icon: 'circle',
        itemWidth: 8, textStyle: { color: '#a3a3a3', fontSize: 10 }
      },
      grid: { left: '2%', right: '2%', bottom: '5%', top: '25%', containLabel: true },
      xAxis: {
        type: 'category',
        data: ['光伏调节\nkW', '储能调节\nkW', '空调调节\nkW', '充电桩调节\nkW', '需量调节\nkVA'],
        axisLine: { show: true, lineStyle: { color: 'rgba(255, 255, 255, 0.1)' } },
        axisTick: { show: false },
        axisLabel: { color: '#a3a3a3', fontSize: 10, lineHeight: 14 }
      },
      yAxis: [
        {
          type: 'value', show: false
        },
        {
          type: 'value', show: false
        }
      ],
      series: [
        {
          name: '实际值', type: 'bar', barWidth: 6,
          data: [12, -18, 0, 654, 34.98],
          itemStyle: { 
            color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{ offset: 0, color: '#00d2ff' }, { offset: 1, color: '#005f73' }]),
            borderRadius: [3,3,0,0]
          },
          label: {
            show: true, position: 'top', color: '#00d2ff', fontSize: 10
          }
        },
        {
          name: '调节目标', type: 'bar', barWidth: 10, barGap: '-135%',
          data: [20, -20, 50, 750, 50],
          itemStyle: { color: 'transparent', borderType: 'dashed', borderColor: '#00ff9d', borderWidth: 1 }
        },
        {
          name: '调节方向', type: 'scatter', symbol: 'rect', symbolSize: [14, 2],
          data: [20, -20, 50, 750, 50],
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