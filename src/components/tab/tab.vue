<template>
  <div class="tab-content">
    <router-link tag="div" class="tab-item" to="/recommend">
      <span class="tab-link">推荐</span>
    </router-link>
    <router-link tag="div" class="tab-item" to="/singer">
      <span class="tab-link">歌手</span>
    </router-link>
    <router-link tag="div" class="tab-item" to="/rank">
      <span class="tab-link">排行</span>
    </router-link>
    <router-link tag="div" class="tab-item" to="/map">
      <span class="tab-link">地图</span>
    </router-link>
  </div>
</template>

<script type="application/ecmascript">
  export default {}
</script>

<style type="text/scss" lang="scss" scoped>
  @import "../../common/scss/variable.scss";
  .tab-content{
    width: 100%;
    position: fixed;
    top:44px;
    z-index:10;
    @include flex();
    height: 44px;
    line-height: 44px;
    font-size:$font-size-medium;
    background:$color-background;
    .tab-item{
      flex: 1;
      text-align: center;
      .tab-link{
        padding-bottom: 5px;
        color: $color-text-l;
      }
    }
    .router-link-active{
      .tab-link{
        color: $color-theme;
        border-bottom: 2px solid $color-theme;
      }
    }
  }
</style>
