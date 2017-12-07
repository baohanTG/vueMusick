<template>
  <div class="vue-content">
      <div class="singer">
        <list-view @select="selectSinger"></list-view>
        <router-view></router-view>
      </div>
  </div>
</template>

<script type="application/ecmascript">
  import ListView from 'base/singerList/singerList'
  import {mapMutations} from 'vuex'
  export default {
    data(){
      return {

      }
    },
    methods:{
      selectSinger(singer) {
        this.$router.push({
           path:`/singer/${singer.id}`
        })
        this.setSinger(singer)
      },
      ...mapMutations({
          setSinger:'SET_SINGER'
      })
    },
    components:{
      ListView
    }
  }
</script>

<style type="text/scss" lang="scss" scoped>
  .singer{
    width: 100%;
    height: auto;
    overflow: hidden;
    position: relative;
  }
</style>
