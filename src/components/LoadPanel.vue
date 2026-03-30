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
    
    // Simulate complex data
    let base = +new Date(2026, 2, 30)
    let oneDay = 24 * 3600 * 1000
    let date = []
    let data = [Math.random() * 300]
    for (let i = 1; i < 50; i++) {
      var now = new Date((base += oneDay))
      date.push([now.getFullYear(), now.getMonth() + 1, now.getDate()].join('/'))
      data.push(Math.round((Math.random() - 0.5) * 20 + data[i - 1]))
    }

    const option = {
      backgroundColor: 'transparent',
      tooltip: { trigger: 'axis', position: function (pt: any) { return [pt[0], '10%']; } },
      title: { left: 'center', text: '楼宇用电量走势', textStyle: { color: '#e2e8f0', fontSize: 14 } },
      toolbox: { feature: { dataZoom: { yAxisIndex: 'none' }, restore: {}, saveAsImage: {} } },
      xAxis: { type: 'category', boundaryGap: false, data: date, axisLine: { lineStyle: { color: '#1e3a8a' } } },
      yAxis: { type: 'value', boundaryGap: [0, '100%'], splitLine: { lineStyle: { color: 'rgba(255, 255, 255, 0.1)' } } },
      dataZoom: [
        { type: 'inside', start: 0, end: 100 },
        { start: 0, end: 100 }
      ],
      series: [
        {
          name: '负载数据', type: 'line', symbol: 'none', sampling: 'lttb',
          itemStyle: { color: 'rgb(14, 165, 233)' },
          areaStyle: {
            color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
              { offset: 0, color: 'rgba(14, 165, 233, 0.8)' },
              { offset: 1, color: 'rgba(14, 165, 233, 0.1)' }
            ])
          },
          data: data
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