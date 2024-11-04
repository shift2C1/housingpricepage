<script setup>
import { defineEmits } from 'vue'
const emit=defineEmits(['setData'])

layui.use(["table"], function () {
  var layer = layui.layer
      , table = layui.table
      , $ = layui.jquery;
  table.render({
    elem: '#demo'
    , height: 315
    // ,width:1000
    , url: 'http://127.0.0.1:8080/get_test_data_list' //数据接口
    , page: true //开启分页

    , cols: [[ //表头
      // {field: 'id', title: 'ID', width:80, sort: true, fixed: 'left'}
      {field: 'longitude', title: '经度', width: 100}
      , {field: 'latitude', title: '纬度', width: 100, sort: true}
      , {field: 'housing_median_age', title: '房子年龄中位数', width: 100}
      , {field: 'total_rooms', title: '房间总数', width: 100}
      , {field: 'total_bedrooms', title: '卧室总数', width: 100, sort: true}
      , {field: 'population', title: '人口总数', width: 100, sort: true}
      , {field: 'households', title: '住户总数', width: 100}
      , {field: 'median_income', title: '收入中位数', width: 100, sort: true}
      , {field: 'ocean_proximity', title: '距离大海', width: 100, sort: true}
      , {fixed: 'right', width: 80, align: 'center', toolbar: "#barDemo"}
    ]]
  });
  table.on('tool(test)', function (obj) { //注：tool是工具条事件名，test是table原始容器的属性 lay-filter="对应的值"
    var data = obj.data; //获得当前行数据
    var layEvent = obj.event; //获得 lay-event 对应的值（也可以是表头的 event 参数对应的值）
    var tr = obj.tr; //获得当前行 tr 的DOM对象

    if (layEvent === 'detail') { //查看
      //do somehing
      layer.msg("msg")
      emit('setData',data)
      console.log(JSON.stringify(data))
    //   给表单赋值
    }
  });


})

</script>


<template>
  <table id="demo" lay-filter="test"></table>

</template>

<style scoped>

</style>