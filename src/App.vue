<script setup lang="ts">
import { onMounted, ref } from 'vue';
const sph = ref("-1");
const cyl = ref("0")
const comName = ref("gdjk")

function praseParas() {
  const params = new URLSearchParams(window.location.search)
  sph.value = params.get("sph") || "n";
  cyl.value = params.get("cyl") || "n";
  comName.value = params.get("comName") || "gdjk";
}

onMounted(() => { praseParas() })

</script>

<template>
  <div>
    <h1>扫码测试</h1>

    <div>
      <div>sph={{ sph }}</div>
      <div>cyl={{ cyl }}</div>
    </div>

    <svg width="400" height="400" style="background: white;">
      <circle cx="200" cy="200" r="175" style="stroke: black;fill: none;" />

      <text x="120" y="190">sph</text>
      <text x="120" y="210">{{ sph }}</text>
      <text x="270" y="190">cyl</text>
      <text x="270" y="210">{{ cyl }}</text>
      <text x="190" y="80">logo</text>
      <text x="190" y="100">{{ comName }}</text>
    </svg>
  </div>
</template>

<style scoped></style>
