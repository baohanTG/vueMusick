<template>
    <div class="vue-swiper">
      <swiper :options="swiperOption" ref="mySwiper">
        <slot></slot>
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
</template>

<script type="application/ecmascript">
  import { swiper, swiperSlide } from 'vue-awesome-swiper'
  export default {
    data(){
      return {
        swiperOption: {
          notNextTick: true,
          autoplay: 1500,
          direction : 'horizontal',
          loop : true,
          initialSlide: 1,
          grabCursor : true,
          setWrapperSize :true,
          autoHeight: true,
          pagination : '.swiper-pagination',
          paginationClickable :true,
          mousewheelControl : true,
          observeParents:true,
          debugger: true,
          autoplayDisableOnInteraction : false
        }
      }
    },
    components: {
      swiper,
      swiperSlide
    }
  }
</script>

<style type="text/scss" lang="scss" scoped>
    .vue-swiper{
      width: 100%;
      height: 40vw;
      position:relative;
      overflow: hidden;
    }
</style>
