<template>
  <view v-if="!cameraActive" class="container">
    <text class="text-color-primary">My Vue Native App</text>
    <text>{{message}}</text>
    <button v-bind:title="buttonText" v-bind:on-press="handleBtnPress" />
  </view>
  <camera-control v-else @back="handleBtnPress" />
</template>

<script>
import CameraControl from "./Components/cameraControl";
export default {
  components: { CameraControl },
  data: function() {
    return {
      message: "Hello World",
      buttonText: "Press Here For Camera",
      cameraActive: false
    };
  },
  methods: {
    handleBtnPress: function() {
      this.cameraActive = !this.cameraActive;
    }
  }
};
</script>

<style>
.container {
  background-color: transparent;
  align-items: center;
  justify-content: center;
  flex: 1;
}
.text-color-primary {
  color: blue;
}
</style>
