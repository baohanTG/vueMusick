<template>
    <div class="vue-content">
        <swiper>
          <swiper-slide class="swiper-item" v-for="item in swipeList">
            <a href="javascript:;">
              <img :src="item.picUrl" alt="">
            </a>
          </swiper-slide>
        </swiper>
      <div class="recommend-list">
          <h1 class="list-title">热门推荐</h1>
          <ul>
              <li v-for="item in displayList" class="item">
                  <div class="icon">
                    <img :src="item.picUrl" alt="" width="60" height="60">
                  </div>
                  <div class="text">
                      <h2 v-html="item.name"></h2>
                      <p v-html="item.description"></p>
                      <p v-html="item.playAmount"></p>
                  </div>
              </li>
          </ul>
      </div>
    </div>
</template>

<script type="application/ecmascript">
  import Swiper from 'base/swipe/swiper'
  import http from 'apiData/http'
  export default {
    name:"test-keep-alive",
    data(){
      return {
        baseul:'',
        swipeList:[],
        displayList:[]
      }
    },
    mounted:function(){
      this.$nextTick(function(){
        this.fetchData();
      });
    },
    methods:{
      fetchData: async function(){
        let params = {}
        const res = await http.get('./static/index.json',params);
        this.swipeList = res.data.slider;
        this.displayList = res.data.songList;
      }
    },
    components: {
      Swiper
    }
  }
</script>

<style type="text/scss" lang="scss" scoped>
  @import "../../common/scss/variable.scss";
  .recommend-list{
    width: 100%;
    height: auto;
    overflow: hidden;
    position: relative;
    .list-title{
      width: 100%;
      text-align: center;
      padding:20px 0px;
      color:$color-theme;
    }
    .item{
      @include flex();
      align-items: center;
      padding: 20px 15px 20px 15px;
      .icon{
        flex: 0 0 60px;
        width: 60px;
         margin-right: 20px;
      }
      .text{
        @include flex();
        @include flex-1();
        flex-direction:column;
        justify-content: center;
        line-height: 20px;
        overflow: hidden;
        font-size: $font-size-medium;
        h2{
          overflow: hidden;
          white-space: nowrap;
          text-overflow: ellipsis;
        }
      }
    }
  }
</style>
