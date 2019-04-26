# vue_sass
vue安装和使用sass
1. 安装依赖：npm install node-sass sass-loader -D
2.webpack.base.conf.js文件
{ //手动添加这一条，相当于是编译识别sass!
 test: /\.scss$/,
loaders: ["style", "css", "sass"]}
 
 }
3. 在.vue文件中使用

<template>
  <div class="outbox">
    <div class="box1">123</div>
    <div class="box2"></div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "Welcome to Your Vue.js App"
    };
  },
  mounted(){
    console.log("%c右侧div宽度:","font-size:16px;color:red",document.getElementsByClassName("box2")[0].offsetWidth)
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
//1920尺寸作为设计稿基准
$vw_base: 1920;
$vh_base: 1080;
@function vw($px) {
  @return ($px / 1920) * 100vw;
}
@function vh($px) {
  @return ($px / 1080) * 100vh;
}
$color: rgb(0, 255, 55);
.outbox {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: flex-start;
  width: 100vw;
  height: 100vh;
/*   background-color: $color; */
  .box1 {
    width: vw(520);
    height: 100vh;
    font-size: vw(14)
    /* background-color: red; */
  }
  .box2 {
    width: 100%;
    height: 100vh;
    background-color: blue;
  }
}
</style>

