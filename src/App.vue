<template>
  <div id="app">
    <m-header></m-header>
    <tab></tab>
    <keep-alive>
       <router-view></router-view>
    </keep-alive>
    <player></player>
  </div>
</template>
<script type="application/ecmascript">
  import MHeader from 'components/m-header/header'
  import Tab from 'components/tab/tab'
  import Player from 'components/palyer/player'
  export default {
    components:{
      MHeader,
      Tab,
      Player
    }
  }
</script>
