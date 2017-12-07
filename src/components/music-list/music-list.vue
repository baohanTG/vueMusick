<template>
  <div class="music-list">
    <div class="back" @click="back">
      <i class="icon-back"></i>
    </div>
    <h1 class="title" v-html="title"></h1>
    <div class="bg-img" :style="bgImg" ref="bgImage">
      <div class="play-wrapper">
        <div class="play" v-show="songs.length>0" ref="playBtn" @click="random">
          <i class="icon-play"></i>
          <span class="text">随机播放全部</span>
        </div>
      </div>
      <div class="filter" ref="filter"></div>
    </div>
    <div class="list" ref="list">
      <div class="song-list-wrapper" ref="wrapper">
        <song-list @select="selectItem" :songs="songs"></song-list>
      </div>
    </div>
  </div>
</template>

<script type="application/ecmascript">
  import SongList from 'base/song-list/song-list'
  import { mapActions } from 'vuex'

  const RESERVED_HEIGHT = 40

  export default {
    props: {
      bgImage: {
        type: String,
        default: ''
      },
      songs: {
        type: Array,
        default: []
      },
      title: {
        type: String,
        default: ''
      }
    },
    computed: {
      bgImg() {
        return `background-image:url(${this.bgImage})`
      }
    },
    mounted() {
      this.imageHeight = this.$refs.bgImage.clientHeight
      this.listHeight = document.documentElement.clientHeight - this.imageHeight
      this.minTransalteY = -this.imageHeight + RESERVED_HEIGHT
      this.$refs.list.style.top = `${this.imageHeight}px`
      this.$refs.list.style.height = `${this.listHeight}px`
    },
    methods: {
      back() {
        this.$router.back()
      },
      selectItem(item, index) {
        this.selectPlay({
          list: this.songs,
          index
        })
      },
      random() {
        this.randomPlay({
          list: this.songs
        })
      },
      ...mapActions([
        'selectPlay',
        'randomPlay'
      ])
    },
    components: {
      SongList
    }
  }
</script>

<style type="text/scss" lang="scss" scoped>
  @import '../../common/scss/variable';

  $imgPlayWidth: 10vw;
  .music-list {
    position: fixed;
    z-index: 100;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    background: $color-background;
    .back {
      position: absolute;
      top: 0;
      left: 6px;
      z-index: 50;
      .icon-back {
        display: inline-block;
        width: $imgPlayWidth;
        height: $imgPlayWidth;
        margin-top: 8px;
      }
      .icon-back:before {
        display: inline-block;
        width: $imgPlayWidth;
        height: $imgPlayWidth;
        content: "";
        background: url("../../common/img/back.svg");
        background-size: cover;
      }
    }
    .title {
      position: absolute;
      top: 0;
      left: 10%;
      z-index: 40;
      width: 80%;
      text-align: center;
      line-height: 40px;
      font-size: $font-size-large;
      color: $color-text;
      @include wap();
    }
    .bg-img {
      position: relative;
      width: 100%;
      height: 0;
      padding-top: 70%;
      transform-origin: top;
      background-size: cover;
      .play-wrapper {
        position: absolute;
        bottom: 20px;
        z-index: 50;
        width: 100%;
        .play {
          width: 135px;
          margin: 0 auto;
          text-align: center;
          border: 1px solid $color-theme;
          color: $color-theme;
          border-radius: 100px;
          font-size: 0;
          .icon-play {
            display: inline-block;
            vertical-align: middle;
            margin-right: 6px;
            font-size: $font-size-medium-x;
          }
          .icon-play:before {
            display: inline-block;
            width: $imgPlayWidth;
            height: $imgPlayWidth;
            content: "";
            background: url("../../common/img/bfqzt.svg");
            background-size: cover;
          }
          .text {
            display: inline-block;
            vertical-align: middle;
            font-size: $font-size-small;
          }
        }
      }
      .filter {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(111, 122, 134, 0.4);
      }
    }
    .list {
      position: fixed;
      top: 0;
      bottom: 0;
      width: 100%;
      background: $color-background;
      overflow: scroll;
    }
  }
</style>
