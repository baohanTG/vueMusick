<template>
  <div class="vue-header">
    <div class="m-header">
      <div class="note" :style="note"></div>
      <h1 class="text">Chicken Music</h1>
    </div>
  </div>
</template>

<script type="application/ecmascript">
  export default {
    data(){
      return{
        note:{
          backgroundImage: "url(" + require("../../assets/logo.png") + ")",
          backgroundSize:"100% 100%"
        }
      }
    }
  }
</script>

<style type="text/scss" lang="scss" scoped>
  @import "../../common/scss/variable.scss";
  .vue-header{
    width: 100%;
    position:fixed;
    top:0;
    z-index:10;
    background:$color-background;
    margin: 0 auto;
    .m-header{
      position: relative;
      height: 44px;
      text-align: center;
      color: $color-theme;
      font-size: 0;
      .note{
        display: inline-block;
        vertical-align: top;
        margin-top: 6px;
        width: 30px;
        height: 32px;
        margin-right: 9px;
      }
      .text{
        display: inline-block;
        vertical-align: top;
        line-height: 44px;
        font-size: $font-size-large;
      }
      .mine{
        position: absolute;
        top: 0;
        right: 0;
        .icon-mine{
          display: block;
          padding: 12px;
          font-size: 20px;
          color: $color-theme;
        }
      }
    }
  }
</style>
