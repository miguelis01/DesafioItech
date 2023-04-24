<template>
  <div>
    <h1 class="mt-5">Dashboard</h1>
    <div class="chart-div">
    </div>
    <BarChart />
    <PieChart :width="500" :height="500"/>
    <RadarChart :width="500" :height="500"/>
  </div>
</template>


