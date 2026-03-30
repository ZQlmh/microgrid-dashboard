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
      tooltip: { formatter: '{a} <br/>{b} : {c}%' },
      series: [
        {
          name: '储能SOC',
          type: 'gauge',
          center: ['50%', '55%'],
          radius: '85%',
          progress: { show: true, width: 18, itemStyle: { color: '#00d2ff' } },
          axisLine: { lineStyle: { width: 18, color: [[1, 'rgba(255,255,255,0.1)']] } },
          axisTick: { show: false },
          splitLine: { length: 15, lineStyle: { width: 2, color: '#999' } },
          axisLabel: { distance: 25, color: '#999', fontSize: 14 },
          anchor: { show: true, showAbove: true, size: 24, itemStyle: { borderWidth: 10 } },
          title: { show: true, color: '#00d2ff', fontSize: 20 },
          detail: {
            valueAnimation: true, fontSize: 50, color: '#fff', formatter: '{value}%', offsetCenter: [0, '70%']
          },
          data: [{ value: 76.5, name: 'State Of Charge' }]
        }
      ]
    }
    myChart.setOption(option)
    
    // Simulate real-time updates
    setInterval(() => {
      const val = +(Math.random() * 20 + 60).toFixed(1)
      myChart?.setOption({ series: [{ data: [{ value: val, name: 'State Of Charge' }] }] })
    }, 3000)

    window.addEventListener('resize', () => myChart?.resize())
  }
}

onMounted(() => initChart())
onUnmounted(() => window.removeEventListener('resize', () => myChart?.resize()))
</script>