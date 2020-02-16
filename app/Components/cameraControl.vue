<template>
  <view class="container">
    <camera class="container" :type="this.type" />
    <button v-bind:title="buttonText" v-bind:on-press="handleBackBtnPress" />
  </view>
</template>

<script>
import {
  Camera,
  Constants,
  getPermissionsAsync,
  requestPermissionsAsync
} from "expo-camera";
export default {
  data: function() {
    return {
      hasCameraPermission: false,
      buttonText: "back to menu",
      type: Constants.Type.back
    };
  },
  mounted: async function() {
    await getPermissionsAsync().then(async status => {
      if (status.status !== "granted") {
        await requestPermissionsAsync()
          .then(status => {
            hasCameraPermission = status.status == "granted" ? true : false;
          })
          .catch(err => {
            console.log(err);
          });
      }
    });
  },
  methods: {
    handleBackBtnPress: function(){
      this.$emit('back')
    }
  },
  components: { Camera }
};
</script>

<style>
.container {
  flex: 1;
}
</style>