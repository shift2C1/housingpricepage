<script setup>
import {ref} from "vue";

const formData = ref([]);
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
// import 'layui-src/dist/css/layui.css';
// import 'layui-src/dist/layui.js';
const setFormData = (data) => {
  formData.value = data;
};

import PredictorForm from "@/components/PredictorForm.vue";
import TestDataList from "@/components/TestDataList.vue";
import Title from "@/components/Title.vue";
import TestDataTitle from "@/components/TestDataTitle.vue";
import V1 from "@/components/v1.vue";

</script>

<template>
  <div class="bg-black u-overflow-visible">
    <div class="ml-20">
      <div class="bg-pink-200 max-w-xs u-border-4 border-red-300  p-1 u-round-md ml-20 mt-5">
      <Title class="text-blue-400"></Title>
    </div>

    <div id="predictform" class="bg-pink-200 max-w-md u-border-4 border-red-300 u-round-md m-5">
      <PredictorForm :formData="formData"></PredictorForm>
    </div>
<!--    <div class="bg-pink-200 max-w-md u-border-4 border-red-300 u-round-md">-->
<!--      <TestDataTitle class="p-1"></TestDataTitle>-->
<!--      <div class="bg-blue-100">-->
<!--      <TestDataList @setData="setFormData"></TestDataList>-->
<!--      </div>-->
<!--    </div>-->
    </div>

  </div>
</template>
<style scoped>
</style>
