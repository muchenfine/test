<script setup>
import { useAxios } from "@vueuse/integrations/useAxios";
import { ref } from "vue";

const query = ref({
  module: ""
});
const { data, isFinished, execute } = useAxios(
  "/api/posts",
  { method: "GET", params: { module: query.value.module } },
  { immediate: false }
);

const options = [
  { label: "餐厅", value: "餐厅" },
  { label: "学校", value: "学校" }
];
</script>

<template>
  <div>
    {{ query }}
    <n-select v-model:value="query.module" size="medium" :options="options" clearable />
    <button @click="execute()">get</button>
  </div>
</template>

<style>
.n-select {
  width: 200px;
}
</style>
