<template>
  <div class="dashboard-header">
    <div class="time-widget" style="position: absolute; left: 30px; color: #00d2ff;">{{ currentTime }}</div>
    <div class="dashboard-title">微电网能源调度驾驶舱 (Microgrid Dashboard)</div>
    <div class="status-widget" style="position: absolute; right: 30px; display: flex; gap: 15px;">
      <el-tag type="success" effect="dark">系统运行正常</el-tag>
      <el-tag type="warning" effect="dark">储能充放电中</el-tag>
    </div>
  </div>
  
  <div class="dashboard-content">
    <!-- Left Column: Grid & PV -->
    <div class="side-column">
      <div class="panel-card">
        <div class="panel-title">主电网交互数据</div>
        <GridPanel />
      </div>
      <div class="panel-card">
        <div class="panel-title">光伏发电矩阵</div>
        <PvPanel />
      </div>
    </div>
    
    <!-- Center Column: Energy Storage & Overview -->
    <div class="center-column">
      <div class="panel-card" style="flex: 1;">
        <div class="panel-title">储能核心枢纽状态</div>
        <StoragePanel />
      </div>
    </div>
    
    <!-- Right Column: Charging Piles & AC Load -->
    <div class="side-column">
      <div class="panel-card">
        <div class="panel-title">充电桩群运行监控</div>
        <ChargingPanel />
      </div>
      <div class="panel-card">
        <div class="panel-title">楼宇空调负载态势</div>
        <LoadPanel />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
import GridPanel from './components/GridPanel.vue'
import PvPanel from './components/PvPanel.vue'
import StoragePanel from './components/StoragePanel.vue'
import ChargingPanel from './components/ChargingPanel.vue'
import LoadPanel from './components/LoadPanel.vue'

const currentTime = ref('')
let timer: ReturnType<typeof setInterval>

const updateTime = () => {
  const now = new Date()
  currentTime.value = now.toLocaleString('zh-CN', { 
    year: 'numeric', month: '2-digit', day: '2-digit', 
    hour: '2-digit', minute: '2-digit', second: '2-digit' 
  })
}

onMounted(() => {
  updateTime()
  timer = setInterval(updateTime, 1000)
})

onUnmounted(() => {
  clearInterval(timer)
})
</script>