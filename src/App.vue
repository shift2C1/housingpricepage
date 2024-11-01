<script setup>
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
// import 'layui-src/dist/css/layui.css';
// import 'layui-src/dist/layui.js';


import PredictorForm from "@/components/PredictorForm.vue";
import TestDataList from "@/components/TestDataList.vue";
</script>

<template>

  <div class="layui-container layui-bg-cyan">
    常规布局（以中型屏幕桌面为例）：
    <div class="layui-row">
      <div class="layui-col-md5">
        你的内容 9/12
        <PredictorForm></PredictorForm>

      </div>
      <div class="layui-col-md5">
        你的内容 3/12
        <TestDataList></TestDataList>
      </div>
    </div>
  </div>

</template>

<style scoped>

</style>
