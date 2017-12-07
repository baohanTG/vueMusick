<template>
  <transition name="slide">
      <music-list :title="title" :bg-image="bgImage" :songs="songs"></music-list>
  </transition>
</template>

<script type="application/ecmascript">
  import MusicList from 'components/music-list/music-list'
  import http from 'apiData/http'
  import { mapGetters } from 'vuex'
  export default {
    data(){
      return {
        songs:[]
      }
    },
    computed:{
      title() {
        return this.singer.name
      },
      bgImage() {
        return this.singer.picUrl
      },
      ...mapGetters([
        'singer'
      ])
    },
    created() {
      this.fetchData();
    },
    methods:{
      fetchData: async function(){
        if(!this.singer.id){
          this.$router.push('/singer');
          return;
        }
        let params = {}
        const res = await http.get('./static/singerDist.json',params);
        this.songs = res.data.list;
      }
    },
    components: {
      MusicList
    }
  }

</script>

<style type="text/scss" lang="scss" scoped>
  @import '../../common/scss/variable';
  .slide-enter-active, .slide-leave-active {
    transition: all 0.3s;
  }
  .slide-enter, .slide-leave-to {
    transform: translate3d(100%, 0, 0);
  }
</style>
