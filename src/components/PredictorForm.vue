<script setup>
import {defineProps, toRefs} from "vue";

const props = defineProps({
  formData: {
    type: [Object, Array],
    default: () => [],
  },
});
const {formData} = toRefs(props);

layui.use(["layer", "form", "jquery", "element"], function () {
  var layer = layui.layer,
      form = layui.form,
      $ = layui.jquery,
      element = layui.element;

  // layer.msg('Hello World');
  form.on("submit(formDemo)", function (data) {
    // layer.msg(JSON.stringify(data.field));
    // console.log(JSON.stringify(data.field))
    $.ajax({
      url: "http://127.0.0.1:8080/predict_price",
      type: "POST",
      contentType: "application/json",
      data: JSON.stringify(data.field),
      success: function (result) {
        const predict_data=result.data
        $("input")[10].value=predict_data.predict_price
      },
    });
    return false;
  });
  $("#viewdata").click(function (data) {
    $.ajax({
      url: "http://127.0.0.1:8080/get_random_test_data",
      type: "GET",
      success: function (result) {
        const obj = result.data[0];
        console.log("随机取数：")
        console.log(obj)
        // 放到表单里
        $("input")[0].value=obj.longitude;
        $("input")[1].value=obj.latitude;
        $("input")[2].value=obj.housing_median_age;
        $("input")[3].value=obj.total_rooms;
        $("input")[4].value=obj.total_bedrooms;
        $("input")[5].value=obj.population;
        $("input")[6].value=obj.households;
        $("input")[7].value=obj.median_income;
        $("input")[8].value=obj.ocean_proximity;

        $("input")[9].value=obj.median_house_value;

        return false
      },
    });
    return false
  });
});
</script>

<template>
  <form class="layui-form" action="">
    <!--    <div class="layui-container">-->
    <!--      -->
    <!--    </div>-->
    <div class="row">
      <div class="col-7">
        <div class="row">
          <div class="col-3">
            <div class="layui-form-item">
              <label class="layui-form-label">经度</label>
              <div class="layui-input-inline">
                <input
                    type="text"
                    name="longitude"
                    placeholder=""
                    autocomplete="off"
                    class="layui-input"
                />
              </div>
            </div>
          </div>

          <div class="col-3">
            <div class="layui-form-item">
              <label class="layui-form-label">维度</label>
              <div class="layui-input-inline">
                <input
                    type="text"
                    name="latitude"
                    placeholder=""
                    autocomplete="off"
                    class="layui-input"
                />
              </div>
            </div>
          </div>
          <div class="col-3">
            <div class="layui-form-item">
              <label class="layui-form-label">房子年龄中位数</label>
              <div class="layui-input-inline">
                <input
                    type="text"
                    name="housing_median_age"
                    placeholder=""
                    autocomplete="off"
                    class="layui-input"
                />
              </div>
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-3">
            <div class="layui-form-item">
              <label class="layui-form-label">房间总数</label>
              <div class="layui-input-inline">
                <input
                    type="text"
                    name="total_rooms"
                    placeholder=""
                    autocomplete="off"
                    class="layui-input"
                />
              </div>
            </div>
          </div>
          <div class="col-3">
            <div class="layui-form-item">
              <label class="layui-form-label">卧室总数</label>
              <div class="layui-input-inline">
                <input
                    type="text"
                    name="total_bedrooms"
                    placeholder=""
                    autocomplete="off"
                    class="layui-input"
                />
              </div>
            </div>
          </div>
          <div class="col-3">
            <div class="layui-form-item">
              <label class="layui-form-label">人口总数</label>
              <div class="layui-input-inline">
                <input
                    type="text"
                    name="population"
                    placeholder=""
                    autocomplete="off"
                    class="layui-input"
                />
              </div>
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-3">
            <div class="layui-form-item">
              <label class="layui-form-label">住户总数</label>
              <div class="layui-input-inline">
                <input
                    type="text"
                    name="households"
                    placeholder=""
                    autocomplete="off"
                    class="layui-input"
                />
              </div>
            </div>
          </div>
          <div class="col-3">
            <div class="layui-form-item">
              <label class="layui-form-label">收入中位数</label>
              <div class="layui-input-inline">
                <input
                    type="text"
                    name="median_income"
                    placeholder=""
                    autocomplete="off"
                    class="layui-input"
                />
              </div>
            </div>
          </div>

          <div class="col-3">
            <div class="layui-form-item">
              <label class="layui-form-label">距离大海</label>
              <div class="layui-input-inline">
                <input
                    type="text"
                    name="ocean_proximity"
                    placeholder=""
                    autocomplete="off"
                    class="layui-input"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="col-5 ">
        <div class="row">
          <div class="col-6">
            <div class="layui-form-item">
              <label class="layui-form-label">真实房价</label>
              <div class="layui-input-inline">
                <input
                    type="text"
                    name="median_house_value"
                    placeholder=""
                    autocomplete="off"
                    class="layui-input"
                />
              </div>
            </div>
          </div>
          <div class="col-6">
            <div class="layui-form-item">
              <label class="layui-form-label">预测房价</label>
              <div class="layui-input-inline">
                <input
                    type="text"
                    name="predict_value"
                    placeholder=""
                    autocomplete="off"
                    class="layui-input"
                />
              </div>
            </div>
          </div>
        </div>

        <div class="row mt-10-lg">
          <div class="col-6">
            <button class="btn-info" lay-submit lay-filter="formDemo">预测房价</button>

          </div>
          <div class="col-6">
            <button id="viewdata" class="btn-success " lay-event="" lay-filter="viewdata">随机测试</button>
          </div>
        </div>

      </div>
    </div>

  </form>
</template>

<style scoped>
</style>