<script setup>
import {defineProps,refs} from 'vue'
const props=defineProps({
  formData:{
    type:[Object,Array],
    default:()=>[]
  }
})
const {formData}=refs(props)
layui.use(['layer', 'form', 'jquery','element'], function () {
  var layer = layui.layer
      , form = layui.form
      , $ = layui.jquery
      ,element = layui.element;

  // layer.msg('Hello World');
  form.on('submit(formDemo)', function (data) {
    // layer.msg(JSON.stringify(data.field));
    // console.log(JSON.stringify(data.field))
    $.ajax({
      url: "http://127.0.0.1:8080/predict_price",
      type: "POST",
      contentType: "application/json",
      data: JSON.stringify(data.field),
      success: function (result) {
        console.log(result)
      }
    });
    return false;
  });
  $("#viewdata").click(function (data) {
    // layer.msg("查看数据")
    console.log("随机取数据")

    return false;
  })
  // form.on("viewdata",function (data) {
  //   alert("事件监听")
  // })
});
</script>

<template>
  <form class="layui-form" action="">
    <div class="layui-container">
      <div class="layui-row">
        <div class="layui-col-md3 ">
          <div class="layui-form-item">
            <label class="layui-form-label">经度</label>
            <div class="layui-input-inline">
              <input type="text" name="longitude"  placeholder="" autocomplete="off"
                     class="layui-input">
            </div>
          </div>
        </div>

        <div class="layui-col-md3">
          <div class="layui-form-item">
            <label class="layui-form-label">维度</label>
            <div class="layui-input-inline">
              <input type="text" name="latitude"  placeholder="" autocomplete="off"
                     class="layui-input">
            </div>
          </div>
        </div>
        <div class="layui-col-md3">
          <div class="layui-form-item">
            <label class="layui-form-label">房子年龄中位数</label>
            <div class="layui-input-inline">
              <input type="text" name="housing_median_age"  placeholder="" autocomplete="off"
                     class="layui-input">
            </div>
          </div>
        </div>
      </div>

      <div class="layui-row">
        <div class="layui-col-md3">
          <div class="layui-form-item">
            <label class="layui-form-label">房间总数</label>
            <div class="layui-input-inline">
              <input type="text" name="total_rooms"  placeholder="" autocomplete="off"
                     class="layui-input">
            </div>
          </div>
        </div>
        <div class="layui-col-md3">
          <div class="layui-form-item">
            <label class="layui-form-label">卧室总数</label>
            <div class="layui-input-inline">
              <input type="text" name="total_bedrooms"  placeholder="" autocomplete="off"
                     class="layui-input">
            </div>
          </div>
        </div>
        <div class="layui-col-md3">
          <div class="layui-form-item">
          <label class="layui-form-label">人口总数</label>
          <div class="layui-input-inline">
            <input type="text" name="population"  placeholder="" autocomplete="off"
                   class="layui-input">
          </div>
        </div>
        </div>
      </div>
      <div class="layui-row">
        <div class="layui-col-md3">
          <div class="layui-form-item">
          <label class="layui-form-label">住户总数</label>
          <div class="layui-input-inline">
            <input type="text" name="households"  placeholder="" autocomplete="off"
                   class="layui-input">
          </div>
        </div>
        </div>
        <div class="layui-col-md3">
          <div class="layui-form-item">
          <label class="layui-form-label">收入中位数</label>
          <div class="layui-input-inline">
            <input type="text" name="median_income"  placeholder="" autocomplete="off"
                   class="layui-input">
          </div>
        </div>
        </div>

        <div class="layui-col-md3">
          <div class="layui-form-item">
          <label class="layui-form-label">距离大海</label>
          <div class="layui-input-inline">
            <input type="text" name="ocean_proximity"  placeholder="" autocomplete="off"
                   class="layui-input">
          </div>
        </div>
        </div>
      </div>
    </div>


    <div class="layui-form-item">
      <div class="layui-input-block">
        <button class="layui-btn" lay-submit lay-filter="formDemo">预测房价</button>
        <button id="viewdata" class="layui-btn layui-btn-normal " lay-event="" lay-filter="viewdata" >随机测试</button>
      </div>
    </div>
  </form>

</template>

<style scoped>

</style>