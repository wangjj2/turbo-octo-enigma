<template>
  <view class="container">
    <text class="text-color-primary">My Vue Native App</text>
    <text>{{message}}</text>
    <button v-bind:title="buttonText" v-bind:on-press="handleBtnPress" />
    <camera-control />
  </view>
</template>

<script>
import CameraControl from "./Components/CameraControl";
export default {
  components: { CameraControl },
  data: function() {
    return {
      message: "Hello World",
      buttonText: "Press Here For Alert"
    };
  },
  methods: {
    handleBtnPress: function() {
      alert("Btn Press");
    }
  }
};
</script>

<style>
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  flex: 1;
}
.text-color-primary {
  color: blue;
}
</style>
