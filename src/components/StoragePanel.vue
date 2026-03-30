<template>
  <div ref="chartRef" class="w-full h-full relative"></div>
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
      title: {
        text: '30%',
        subtext: '当前电量',
        left: 'center',
        top: 'center',
        textStyle: { color: '#fff', fontSize: 24, fontWeight: 'bold' },
        subtextStyle: { color: '#a3a3a3', fontSize: 10, padding: [5,0,0,0] }
      },
      series: [
        {
          name: 'SOC',
          type: 'pie',
          radius: ['70%', '85%'],
          avoidLabelOverlap: false,
          label: { show: false },
          labelLine: { show: false },
          data: [
            { 
              value: 30, 
              name: 'Remaining',
              itemStyle: { 
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                  { offset: 0, color: '#00d2ff' },
                  { offset: 1, color: '#005f73' }
                ]),
                shadowBlur: 10, shadowColor: '#00d2ff'
              }
            },
            { 
              value: 70, 
              name: 'Used',
              itemStyle: { color: 'rgba(255, 255, 255, 0.1)' }
            }
          ]
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