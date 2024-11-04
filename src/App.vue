<script setup>
import torefs from 'vue'
const formData=torefs([])
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
// import 'layui-src/dist/css/layui.css';
// import 'layui-src/dist/layui.js';
const setFormData=(data)=>{
  formData.value=data
}

import PredictorForm from "@/components/PredictorForm.vue";
import TestDataList from "@/components/TestDataList.vue";
import Title from "@/components/Title.vue";
import TestDataTitle from "@/components/TestDataTitle.vue";
</script>

<template>
  <div class="layui-bg-orange">
    <Title></Title>
  </div>

  <div id="predictform" class="bg-color">
    <PredictorForm :formData="formData"></PredictorForm>
  </div>
  <div class="layui-bg-orange" >
    <TestDataTitle></TestDataTitle>
  </div>
  <div class="bg-color" >
    <TestDataList @setData="setFormData"></TestDataList>
  </div>

</template>
<style scoped>

</style>
