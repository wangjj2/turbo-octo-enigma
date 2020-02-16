<template>
  <view class="container">
    <camera class="container" :type="this.type" />
  </view>
</template>

<script>
import {
  Camera,
  getPermissionsAsync,
  requestPermissionsAsync
} from "expo-camera";
export default {
  data: function() {
    return {
      hasCameraPermission: false,
      type: Camera.Constants.Type.back
    };
  },
  mounted: async function() {
    await getPermissionsAsync().then(async status => {
      if (!status.status) {
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
  components: { Camera }
};
</script>

<style>
.text-color-primary {
  color: blue;
}
</style>