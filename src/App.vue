<template>
  <div class="h-screen w-screen flex flex-col p-4 gap-4 box-border relative">
    
    <!-- Header -->
    <header class="h-[70px] flex-shrink-0 flex items-center justify-between px-8 header-bg relative z-20">
      <div class="flex items-center gap-4 text-xs font-mono text-gray-400">
        <span class="text-[#00d2ff] font-bold">2022年9月22日</span>
        <span>春分 星期四 工作日</span>
        <span class="text-white text-sm bg-white/10 px-2 py-1 rounded">11:46:23 申时</span>
      </div>
      
      <div class="absolute left-1/2 -translate-x-1/2 top-4 flex flex-col items-center">
        <h1 class="text-3xl font-extrabold tracking-[4px] text-gradient pb-2 drop-shadow-md">广联达电能优化运行概览</h1>
      </div>

      <div class="flex items-center gap-4 text-xs font-mono text-gray-400">
        <span class="flex items-center gap-2">今日天气: 晴 <span class="text-yellow-400">☀️</span> 优 17/7°C</span>
        <span class="flex items-center gap-2 border-l border-white/20 pl-4">明日天气: 阴 ☁️ 良 21/8°C</span>
      </div>
    </header>

    <!-- Main Content -->
    <main class="flex-1 grid grid-cols-12 gap-5 overflow-hidden z-10">
      
      <!-- Left Column (3/12) -->
      <div class="col-span-3 flex flex-col gap-5 h-full">
        <!-- 总览 -->
        <div class="tech-panel h-[25%] flex flex-col">
          <div class="panel-header">
            <span class="panel-title">数据总览 Data Overview</span>
          </div>
          <div class="flex-1 grid grid-cols-2 grid-rows-3 gap-2 p-4 text-xs">
            <!-- Items -->
            <div class="flex items-center gap-3">
              <div class="w-10 h-10 bg-[#00ff9d]/10 rounded-lg flex items-center justify-center border border-[#00ff9d]/30">🔋</div>
              <div><div class="text-gray-400">年发电量【源】</div><div class="text-[#00ff9d] text-xl font-mono font-bold">260 <span class="text-xs">万度</span></div></div>
            </div>
            <div class="flex items-center gap-3">
              <div class="w-10 h-10 bg-[#00d2ff]/10 rounded-lg flex items-center justify-center border border-[#00d2ff]/30">🔌</div>
              <div><div class="text-gray-400">年余电上网【网】</div><div class="text-[#00d2ff] text-xl font-mono font-bold">120 <span class="text-xs">万度</span></div></div>
            </div>
            <div class="flex items-center gap-3">
              <div class="w-10 h-10 bg-[#00ff9d]/10 rounded-lg flex items-center justify-center border border-[#00ff9d]/30">📉</div>
              <div><div class="text-gray-400">年节电量【荷储】</div><div class="text-[#00ff9d] text-xl font-mono font-bold">20 <span class="text-xs">万度</span></div></div>
            </div>
            <div class="flex items-center gap-3">
              <div class="w-10 h-10 bg-[#00d2ff]/10 rounded-lg flex items-center justify-center border border-[#00d2ff]/30">♻️</div>
              <div><div class="text-gray-400">新能源消纳率</div><div class="text-[#00d2ff] text-xl font-mono font-bold">90%</div></div>
            </div>
            <div class="flex items-center gap-3">
              <div class="w-10 h-10 bg-[#00ff9d]/10 rounded-lg flex items-center justify-center border border-[#00ff9d]/30">💰</div>
              <div><div class="text-gray-400">年总收益</div><div class="text-[#00ff9d] text-xl font-mono font-bold">260 <span class="text-xs">万元</span></div></div>
            </div>
            <div class="flex items-center gap-3">
              <div class="w-10 h-10 bg-[#00d2ff]/10 rounded-lg flex items-center justify-center border border-[#00d2ff]/30">🌱</div>
              <div><div class="text-gray-400">年节碳量</div><div class="text-[#00d2ff] text-xl font-mono font-bold">260 <span class="text-xs">吨</span></div></div>
            </div>
          </div>
        </div>
        
        <!-- 策略运行状态 -->
        <div class="tech-panel h-[35%] flex flex-col">
          <div class="panel-header">
            <span class="panel-title">策略运行状态 Control Strategy</span>
            <span class="text-[#00ff9d] text-xs font-bold px-2 py-0.5 border border-[#00ff9d]/40 rounded bg-[#00ff9d]/10">光储直柔-成本策略 运行中</span>
          </div>
          <div class="p-4 flex flex-col gap-4">
            <div class="flex items-center gap-6 bg-white/5 p-4 rounded-xl border border-white/10">
              <div>
                <div class="text-gray-400 text-xs mb-1">当日用电总量</div>
                <div class="text-2xl font-mono font-bold">110 <span class="text-sm">万度</span></div>
              </div>
              <div class="h-10 w-px bg-white/20"></div>
              <div class="flex-1">
                <div class="flex justify-between text-xs text-gray-400 mb-2"><span>自供电率(%)</span></div>
                <div class="flex gap-1 h-6">
                  <div class="flex-1 bg-[#00ff9d] rounded-sm shadow-[0_0_8px_#00ff9d]"></div>
                  <div class="flex-1 bg-[#00ff9d] rounded-sm shadow-[0_0_8px_#00ff9d] opacity-90"></div>
                  <div class="flex-1 bg-[#00ff9d] rounded-sm shadow-[0_0_8px_#00ff9d] opacity-80"></div>
                  <div class="flex-1 bg-white/20 rounded-sm"></div>
                  <div class="flex-1 bg-white/20 rounded-sm"></div>
                  <div class="flex-1 bg-white/20 rounded-sm"></div>
                  <div class="flex-1 bg-white/20 rounded-sm"></div>
                </div>
              </div>
            </div>
            <div class="grid grid-cols-4 gap-2 text-center text-xs mt-2">
              <div><div class="text-gray-400 mb-1">并网点功率</div><div class="font-mono text-lg">110<span class="text-[10px]">kW</span></div><div class="text-[#ffb13b] scale-90">环比 3.91%↑</div></div>
              <div><div class="text-gray-400 mb-1">当日碳排量</div><div class="font-mono text-lg">110<span class="text-[10px]">吨</span></div><div class="text-[#00ff9d] scale-90">环比 3.91%↓</div></div>
              <div><div class="text-gray-400 mb-1">当日减碳量</div><div class="font-mono text-lg">110<span class="text-[10px]">吨</span></div><div class="text-[#ffb13b] scale-90">环比 3.91%↑</div></div>
              <div><div class="text-gray-400 mb-1">当日费用</div><div class="font-mono text-lg">11<span class="text-[10px]">万元</span></div><div class="text-[#00ff9d] scale-90">环比 3.91%↓</div></div>
            </div>
          </div>
        </div>
        
        <!-- 实时策略可视化 -->
        <div class="tech-panel h-[40%] flex flex-col">
          <div class="panel-header">
            <span class="panel-title">实时策略可视化 Strategy Visual</span>
          </div>
          <div class="flex-1 p-2">
             <LoadPanel />
          </div>
        </div>
      </div>

      <!-- Center Column (5/12) -->
      <div class="col-span-6 flex flex-col gap-5 h-full relative">
        <!-- Top 3D View Placeholder & Floating Cards -->
        <div class="flex-1 rounded-xl relative overflow-hidden bg-[url('https://images.unsplash.com/photo-1451187580459-43490279c0fa?q=80&w=2072&auto=format&fit=crop')] bg-cover bg-center">
          <!-- Dark overlay -->
          <div class="absolute inset-0 bg-[#040b14]/80 backdrop-blur-sm z-0"></div>
          
          <!-- Central Network Visualization (Mock) -->
          <div class="absolute inset-0 z-10 flex items-center justify-center">
             <!-- Building Cube Mock -->
             <div class="w-32 h-40 bg-white/10 border-2 border-[#00d2ff] rounded backdrop-blur-md shadow-[0_0_30px_#00d2ff55] relative flex flex-col items-center justify-center">
                <div class="text-[#00d2ff] font-bold text-lg mb-2">配电室</div>
                <div class="text-xs text-center border-t border-[#00d2ff]/30 pt-2 w-full">
                  <div class="text-gray-300">当日上网电量 <span class="text-white font-mono">36 kWh</span></div>
                  <div class="text-gray-300">当日费用预估 <span class="text-white font-mono">36 元</span></div>
                </div>
             </div>
             
             <!-- Floating Cards mimicking design -->
             <div class="absolute top-[15%] left-[10%] bg-[#0c2135]/90 border border-[#00ff9d]/40 rounded-lg p-3 text-xs shadow-lg backdrop-blur">
               <div class="text-[#00ff9d] font-bold mb-2 flex justify-between w-32"><span>🔋 储能</span> <span class="text-white/50 text-[10px]">详情 ></span></div>
               <div class="flex justify-between text-gray-300 mb-1"><span>实时发电功率</span> <span class="font-mono text-white">36 kW</span></div>
               <div class="flex justify-between text-gray-300 mb-1"><span>实时电池容量</span> <span class="font-mono text-white">36 kWh</span></div>
               <div class="flex justify-between text-gray-300"><span>当日累计收益</span> <span class="font-mono text-white">36 元</span></div>
             </div>

             <div class="absolute top-[10%] right-[30%] bg-[#0c2135]/90 border border-[#00d2ff]/40 rounded-lg p-3 text-xs shadow-lg backdrop-blur">
               <div class="text-[#00d2ff] font-bold mb-2">💡 其他柔性负荷</div>
               <div class="flex justify-between text-gray-300 mb-1 w-32"><span>实时功率</span> <span class="font-mono text-white">36 kW</span></div>
               <div class="flex justify-between text-gray-300"><span>当日节电收益</span> <span class="font-mono text-white">36 元</span></div>
             </div>

             <div class="absolute bottom-[20%] left-[5%] bg-[#0c2135]/90 border border-[#00ff9d]/40 rounded-lg p-3 text-xs shadow-lg backdrop-blur">
               <div class="text-[#00ff9d] font-bold mb-2 flex justify-between w-32"><span>☀️ 光伏</span> <span class="text-white/50 text-[10px]">详情 ></span></div>
               <div class="flex justify-between text-gray-300 mb-1"><span>实时发电功率</span> <span class="font-mono text-white">36 kW</span></div>
               <div class="flex justify-between text-gray-300"><span>当日收益</span> <span class="font-mono text-white">36 元</span></div>
             </div>

             <div class="absolute top-[30%] right-[5%] bg-[#0c2135]/90 border border-[#00d2ff]/40 rounded-lg p-3 text-xs shadow-lg backdrop-blur">
               <div class="text-[#00d2ff] font-bold mb-2 flex justify-between w-32"><span>❄️ 空调</span> <span class="text-white/50 text-[10px]">详情 ></span></div>
               <div class="flex justify-between text-gray-300 mb-1"><span>实时功率</span> <span class="font-mono text-white">36 kW</span></div>
               <div class="flex justify-between text-gray-300"><span>当日节电收益</span> <span class="font-mono text-white">36 元</span></div>
             </div>

             <!-- Connection lines mockup -->
             <svg class="absolute inset-0 w-full h-full pointer-events-none -z-10">
               <line x1="25%" y1="30%" x2="50%" y2="50%" stroke="rgba(0, 255, 157, 0.4)" stroke-width="2" stroke-dasharray="4" />
               <line x1="20%" y1="70%" x2="50%" y2="50%" stroke="rgba(0, 255, 157, 0.4)" stroke-width="2" stroke-dasharray="4" />
               <line x1="70%" y1="20%" x2="50%" y2="50%" stroke="rgba(0, 210, 255, 0.4)" stroke-width="2" stroke-dasharray="4" />
               <line x1="85%" y1="40%" x2="50%" y2="50%" stroke="rgba(0, 210, 255, 0.4)" stroke-width="2" stroke-dasharray="4" />
             </svg>
          </div>
        </div>

        <!-- 实时运行状态曲线 -->
        <div class="tech-panel h-[35%] flex flex-col">
          <div class="panel-header">
            <span class="panel-title">实时运行状态曲线 Power Grid Curve</span>
            <div class="bg-white/10 px-3 py-1 rounded text-xs font-mono border border-white/20 text-[#00d2ff]">2024年12月28日 ﹀</div>
          </div>
          <div class="flex-1 p-2">
            <GridPanel />
          </div>
        </div>
      </div>

      <!-- Right Column (4/12) -->
      <div class="col-span-3 flex flex-col gap-5 h-full">
        <!-- 光伏运行情况 -->
        <div class="tech-panel h-[20%] flex flex-col">
          <div class="panel-header">
            <span class="panel-title">光伏运行情况 PV Supply</span>
            <span class="text-[#00ff9d] text-xs flex items-center gap-1"><span class="w-1.5 h-1.5 rounded-full bg-[#00ff9d] animate-pulse"></span> 发电中</span>
          </div>
          <div class="p-4 flex justify-between items-end h-full">
            <div>
              <div class="text-xs text-gray-400 mb-1">实时发电功率</div>
              <div class="text-3xl font-mono font-bold text-white">240 <span class="text-sm font-sans text-[#00ff9d]">kW</span></div>
              <div class="w-full h-1.5 bg-white/10 rounded-full mt-2 overflow-hidden"><div class="w-[70%] h-full bg-[#00ff9d] shadow-[0_0_10px_#00ff9d]"></div></div>
            </div>
            <div>
              <div class="text-xs text-gray-400 mb-1">预测发电功率</div>
              <div class="text-3xl font-mono font-bold text-white">340 <span class="text-sm font-sans text-gray-400">kW</span></div>
              <div class="w-full h-1.5 bg-white/10 rounded-full mt-2 overflow-hidden"><div class="w-[100%] h-full bg-white/40"></div></div>
            </div>
            <div class="text-right">
              <div class="text-xs text-gray-400 mb-1">今日发电量</div>
              <div class="text-xl font-mono font-bold">36<span class="text-[10px] text-gray-400 ml-1">kW·h</span></div>
            </div>
          </div>
        </div>
        
        <!-- 储能运行情况 -->
        <div class="tech-panel h-[30%] flex flex-col">
          <div class="panel-header">
            <span class="panel-title">储能运行情况 Storage</span>
            <span class="text-[#00d2ff] text-xs flex items-center gap-1"><span class="w-1.5 h-1.5 rounded-full bg-[#00d2ff] animate-pulse"></span> 放电中</span>
          </div>
          <div class="flex-1 p-2 flex">
            <!-- SOC Gauge Placeholder -->
            <div class="w-1/3 relative flex flex-col items-center justify-center">
               <StoragePanel />
            </div>
            <!-- Trend Line -->
            <div class="w-2/3 p-2 relative">
               <PvPanel />
            </div>
          </div>
        </div>
        
        <!-- 负荷运行情况 -->
        <div class="tech-panel h-[30%] flex flex-col">
          <div class="panel-header">
            <span class="panel-title">负荷运行情况 Load</span>
            <span class="text-[#00ff9d] text-xs px-2 py-0.5 border border-[#00ff9d]/30 rounded-full">自控中</span>
          </div>
          <div class="p-4 grid grid-cols-4 gap-2 text-center text-white border-b border-white/10 pb-3 mb-2">
            <div><div class="text-xs text-gray-400 mb-1">空调</div><div class="font-mono text-lg font-bold">50.00<span class="text-[10px] text-gray-400 ml-0.5">kW</span></div></div>
            <div><div class="text-xs text-gray-400 mb-1">充电桩充电</div><div class="font-mono text-lg font-bold">25.00<span class="text-[10px] text-gray-400 ml-0.5">kW</span></div></div>
            <div><div class="text-xs text-gray-400 mb-1">充电桩放电</div><div class="font-mono text-lg font-bold">10.00<span class="text-[10px] text-gray-400 ml-0.5">kW</span></div></div>
            <div><div class="text-xs text-gray-400 mb-1">其他</div><div class="font-mono text-lg font-bold">15.00<span class="text-[10px] text-gray-400 ml-0.5">kW</span></div></div>
          </div>
          <div class="flex-1 p-2">
            <ChargingPanel />
          </div>
        </div>

        <!-- 需求响应 -->
        <div class="tech-panel h-[20%] flex flex-col">
          <div class="panel-header">
            <span class="panel-title">需求响应 Virtual Power Plant</span>
            <span class="text-gray-400 text-xs px-2 py-0.5 border border-gray-500/30 rounded-full">待响应</span>
          </div>
          <div class="p-4 text-xs">
            <div class="text-[#00ff9d] mb-1 font-bold">[调峰需求] 广联达信息大厦邀约于2023-11-30 12:00 ~ 2023-11-30 13:00 调峰 10kW</div>
            <div class="text-gray-500 font-mono">2023-11-30 12:12:34</div>
          </div>
        </div>

      </div>
    </main>
  </div>
</template>

<script setup lang="ts">
import GridPanel from './components/GridPanel.vue'
import PvPanel from './components/PvPanel.vue'
import StoragePanel from './components/StoragePanel.vue'
import ChargingPanel from './components/ChargingPanel.vue'
import LoadPanel from './components/LoadPanel.vue'
</script>