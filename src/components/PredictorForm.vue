<script setup>
layui.use(['layer', 'form','jquery'], function () {
  var layer = layui.layer
      , form = layui.form
      ,$=layui.jquery;

  // layer.msg('Hello World');
  form.on('submit(formDemo)', function(data){
    // layer.msg(JSON.stringify(data.field));
    console.log(JSON.stringify(data.field))
    // $.ajax({
    //   url:"127.0.0.1:8080/predictprice",
    //   data:JSON.stringify(data.field),
    //   success:function(result){
    //     console.log(result)
    // }});
    return false;
  });
});
</script>

<template>
<form class="layui-form" action="">
          <div class="layui-form-item">
            <label class="layui-form-label">输入框</label>
            <div class="layui-input-inline">
              <input type="text" name="title" required lay-verify="required" placeholder="请输入标题" autocomplete="off"
                     class="layui-input">
            </div>
          </div>

          <div class="layui-form-item">
            <div class="layui-input-block">
              <button class="layui-btn" lay-submit lay-filter="formDemo">立即提交</button>
              <button type="reset" class="layui-btn layui-btn-primary">重置</button>
            </div>
          </div>
        </form>
</template>

<style scoped>

</style>