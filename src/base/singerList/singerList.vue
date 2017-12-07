<template>
  <div class="listview">
      <ul>
        <li  class="list-group">
          <h2 class="list-group-title">热门</h2>
          <uL>
            <li @click="selectItem(item)" v-for="item in singerList" class="list-group-item">
              <img class="avatar" :src="item.picUrl">
              <span class="name">{{item.name}}</span>
            </li>
          </uL>
        </li>
      </ul>
  </div>
</template>
<script type="application/ecmascript">
  import http from 'apiData/http'
    export default {
      data(){
        return {
          singerList:[]
        }
      },
      created(){
        this.fetchData();
      },
      methods:{
        selectItem(item){
          this.$emit('select',item);
        },
        fetchData: async function(){
          let params = {}
          const res = await http.get('./static/singer.json',params);
          this.singerList = res.data.singerList;
        }
      }
    }
</script>

<style type="text/scss" lang="scss" scoped>
  @import "../../common/scss/variable.scss";
  .listview{
    position: relative;
    width: 100%;
    height: 100%;
    overflow: hidden;
    background: $color-background;
    .list-group{
      padding-bottom: 30px;
      .list-group-title{
        width: 100%;
        position: fixed;
        top:88px;
        height: 30px;
        line-height: 30px;
        padding-left: 20px;
        font-size: $font-size-small;
        color: $color-text-l;
        background: $color-highlight-background;
      }
      ul{
        padding-top:23px;
        .list-group-item{
          display: flex;
          align-items: center;
          padding: 20px 0 0 30px;
          .avatar{
            width: 50px;
            height: 50px;
            border-radius: 50%;
          }
          .name{
            margin-left: 20px;
            color: $color-text-l;
            font-size: $font-size-medium;
          }
        }
      }
    }
  }

</style>
