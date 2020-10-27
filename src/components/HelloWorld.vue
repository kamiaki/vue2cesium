<template>
  <vc-viewer class="viewer" :animation="animation" :timeline="timeline" :camera.sync="camera" @ready="ready">
    <vc-layer-imagery>
      <vc-provider-imagery-openstreetmap></vc-provider-imagery-openstreetmap>
    </vc-layer-imagery>
  </vc-viewer>
</template>
<script>
export default {
  data () {
    return {
      animation: true,
      timeline: true,
      camera: {
        position: {
          lng: 104.06,
          lat: 30.67,
          height: 100000
        },
        heading: 360,
        pitch: -90,
        roll: 0
      }
    }
  },
  methods: {
    ready (cesiumInstance) {
      const { Cesium, viewer } = cesiumInstance
      viewer.entities.add({
        id: '成都欢迎你',
        position: Cesium.Cartesian3.fromDegrees(104.06, 30.67, 100),
        billboard: new Cesium.BillboardGraphics({
          image: 'https://zouyaoji.top/vue-cesium/favicon.png',
          scale: 0.1
        }),
        label: new Cesium.LabelGraphics({
          text: 'Hello Word',
          fillColor: Cesium.Color.GOLD,
          font: '24px sans-serif',
          horizontalOrigin: 1,
          outlineColor: new Cesium.Color(0, 0, 0, 1),
          outlineWidth: 2,
          pixelOffset: new Cesium.Cartesian2(17, -5),
          style: Cesium.LabelStyle.FILL
        })
      })
    }
  }
}
</script>
<style>
  .viewer {
    width: 100%;
    height: 100%;
  }
</style>
