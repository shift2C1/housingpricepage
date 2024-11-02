<script setup>
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
// import 'layui-src/dist/css/layui.css';
// import 'layui-src/dist/layui.js';


import PredictorForm from "@/components/PredictorForm.vue";
import TestDataList from "@/components/TestDataList.vue";
import Title from "@/components/Title.vue";
</script>

<template>
  <div>
    <Title></Title>
  </div>

  <div id="predictform" class="layui-bg-black">
    <PredictorForm></PredictorForm>
  </div>
  <div>
    测试数据
  </div>
  <div class="layui-bg-cyan">
    <TestDataList></TestDataList>
  </div>



</template>

<style scoped>

</style>
