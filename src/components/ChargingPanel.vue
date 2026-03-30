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
        data: ['实际需量', '预测需量', '实际用电量', '预测电量'],
        top: 0, right: 0, icon: 'circle',
        itemWidth: 8, textStyle: { color: '#a3a3a3', fontSize: 10 }
      },
      grid: { left: '2%', right: '2%', bottom: '5%', top: '25%', containLabel: true },
      xAxis: {
        type: 'category',
        data: ['1月', '2月', '3月', '4月', '5月', '6月', '7月', '8月', '9月', '10月', '11月', '12月'],
        axisLine: { show: false },
        axisTick: { show: false },
        axisLabel: { color: '#a3a3a3', fontSize: 9 }
      },
      yAxis: [
        {
          type: 'value', name: '用电量/万度',
          nameTextStyle: { color: '#a3a3a3', fontSize: 9, align: 'left', padding: [0, 0, 0, -20] },
          splitLine: { lineStyle: { color: 'rgba(255, 255, 255, 0.05)', type: 'dashed' } },
          axisLabel: { color: '#a3a3a3', fontSize: 9 }, min: 0, max: 300
        },
        {
          type: 'value', name: '需量/kVA',
          nameTextStyle: { color: '#a3a3a3', fontSize: 9, align: 'right', padding: [0, -20, 0, 0] },
          splitLine: { show: false },
          axisLabel: { color: '#a3a3a3', fontSize: 9 }, min: 0, max: 240
        }
      ],
      series: [
        {
          name: '实际用电量', type: 'bar', barWidth: 6,
          data: [180, 160, 200, 210, 240, 250, 260, 260, 240, 200, 190, 180],
          itemStyle: { 
            color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{ offset: 0, color: '#00d2ff' }, { offset: 1, color: 'transparent' }]) 
          }
        },
        {
          name: '预测电量', type: 'bar', barWidth: 6, barGap: '-100%',
          data: [190, 170, 210, 220, 250, 260, 270, 270, 250, 210, 200, 190],
          itemStyle: { color: 'transparent', borderType: 'dashed', borderColor: '#00d2ff', borderWidth: 1 }
        },
        {
          name: '实际需量', type: 'line', yAxisIndex: 1, symbol: 'circle', symbolSize: 6,
          data: [100, 90, 120, 130, 150, 160, 170, 170, 150, 120, 110, 100],
          itemStyle: { color: '#00ff9d' }
        },
        {
          name: '预测需量', type: 'line', yAxisIndex: 1, symbol: 'none',
          data: [110, 100, 130, 140, 160, 170, 180, 180, 160, 130, 120, 110],
          itemStyle: { color: '#a3a3a3' }, lineStyle: { type: 'dashed' }
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