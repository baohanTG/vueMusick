<template>
  <div class="vue-content">
    <div class="vue-rank">
      <ul>
        <li class="item" v-for="item in topList">
          <div class="icon">
            <img width="100" height="100" :src="item.picUrl"/>
          </div>
          <ul class="songlist">
            <li class="song" v-for="(song,index) in item.songList">
              <span>{{index + 1}}</span>
              <span>{{song.songname}}-{{song.singername}}</span>
            </li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</template>

<script type="application/ecmascript">
  import http from 'apiData/http'
  export default {
    data(){
      return {
        topList:[]
      }
    },
    created(){
      this.fetchData();
    },
    methods:{
      fetchData: async function(){
        let params = {}
        const res = await http.get('./static/rank.json',params);
        this.topList = res.data.topList;
      }
    }
  }

</script>

<style type="text/scss" lang="scss" scoped>
  @import "../../common/scss/variable.scss";
  .vue-rank {
    width: 100%;
    height: auto;
    overflow: hidden;
    position: relative;
    .item{
      width: 90%;
      margin: 0 auto;
      @include flex();
      height: 100px;
      margin-top:20px;
      margin-bottom:20px;
      &:last-child{
        padding-bottom: 20px;
      }
      .icon{
        flex: 0 0 100px;
        width: 100px;
        height: 100px;
      }
      .songlist{
        @include flex();
        @include flex-1();
        flex-direction: column;
        justify-content: center;
        padding: 0 20px;
        height: 100px;
        overflow: hidden;
        background: $color-highlight-background;
        color: $color-text-d;
        font-size: $font-size-small;
      }
      .song{
        @include wap();
        line-height: 26px;
      }
    }
  }
</style>
