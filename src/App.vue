<script setup lang="ts">
import { onMounted, ref } from 'vue';
const brand = ref("GDJK");
const sph = ref("-1");
const cyl = ref("0");
const lind = ref("1.56");
const comName = ref("江苏工大金凯高端装备制造有限公司");
const prodDate = ref("2026年3月6日");
const job = ref("GDJK20260306-1.56-00001");
const isGenSvg = ref(false);

function praseParas() {
  const params = new URLSearchParams(window.location.search)
  brand.value = params.get("brand") || "n";
  sph.value = params.get("sph") || "n";
  cyl.value = params.get("cyl") || "n";
  lind.value = params.get("lind") || "n";
  comName.value = params.get("comName") || "n";
  prodDate.value = params.get("prodDate") || "n";
  job.value = params.get("job") || "n";
  isGenSvg.value = params.get("isGenSvg") == "true" || false;
}

onMounted(() => { praseParas() })

</script>

<template>
  <div>
    <h1 style="text-align: center;">江苏工大金凯高端装备制造有限公司</h1>

    <svg v-if="isGenSvg" width="400" height="400" style="background: white;">
      <circle cx="200" cy="200" r="175" style="stroke: black;fill: none;" />

      <text x="120" y="190">sph</text>
      <text x="120" y="210">{{ sph }}</text>
      <text x="270" y="190">cyl</text>
      <text x="270" y="210">{{ cyl }}</text>
      <text x="190" y="80">{{ comName }}</text>
      <text x="190" y="100">{{ brand }}</text>
    </svg>

    <table class="table">
      <tbody>
        <tr>
          <td>镜片品牌</td>
          <td>{{ brand }}</td>
        </tr>
        <tr>
          <td>镜片折射率</td>
          <td>{{ lind }}</td>
        </tr>
        <tr>
          <td>镜片光度</td>
          <td>SPH:{{ sph }} CYL:{{ cyl }}</td>
        </tr>
        <tr>
          <td>生产商</td>
          <td>{{ comName }}</td>
        </tr>
        <tr>
          <td>生产日期</td>
          <td>{{ prodDate }}</td>
        </tr>
        <tr>
          <td>产品编号</td>
          <td>{{ job }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.table {
  width: 100%;
  border-collapse: collapse;
  margin: 20px 0;
}

.table td {
  text-align: center;
  border: 1px solid black;
}

.table td:nth-child(1) {
  width: 30%;
}

.table td:nth-child(2) {
  width: 70%;
}
</style>
