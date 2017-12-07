<template>
  <div class="vue-content">
    <div id="container" style="width: 100%;height:140vw; margin: 0 auto;"></div>
  </div>
</template>

<script type="application/ecmascript">
  import AMap from 'AMap'
  var map
  export default {
    mounted: function () {
      this.init()
    },
    methods: {
      init: function () {
        map = new AMap.Map('container', {
          pitch:75,
          viewMode:'3D',
          zoom: 18,
          expandZoomRange:true,
          zooms:[3,20],
          center:[116.46689, 39.89887]
        });

      }
    }
  }
</script>
