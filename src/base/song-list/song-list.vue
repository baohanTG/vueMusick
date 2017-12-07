<template>
  <div class="song-list">
    <ul>
      <li @click="selectItem(item,index)" class="item" v-for="(item,index) in songs">
        <h2 class="song-name">{{item.musicName}}</h2>
        <p class="song-des">{{item.musicAlbum}}</p>
      </li>
    </ul>
  </div>
</template>

<script type="application/ecmascript">
  export default {
    props: {
      songs: {
        type: Array,
        default: []
      }
    },
    methods: {
      selectItem(item, index) {
        this.$emit('select', item, index)
      }
    }
  }
</script>

<style type="text/scss" lang="scss" scoped>
  @import "../../common/scss/variable";
  .song-list {
    width: 100%;
    height: auto;
    ul {
      margin-top: 15px;
      margin-bottom: 65px;
      .item {
        width: 100%;
        overflow: hidden;
        padding: 5px 25px;
        h2, p {
          @include wap();
          padding: 5px 0px;
        }
        .song-name {
          color: $color-text
        }
        .song-des {
          color: $color-text-d
        }
      }
    }
  }
</style>
