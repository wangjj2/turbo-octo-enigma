<template>
  <view class="container">
    <camera class="container" :type="this.type" />
  </view>
</template>

<script>
import { Camera, getPermissionsAsync, requestPermissionsAsync } from "expo-camera";
export default {
 data: function() {
   return {
     hasCameraPermission: false,
     type: Camera.Constants.Type.back,
   };
 },
 mounted: async function() {
   await getPermissionsAsync().then(status=>{
     hasCameraPermission = status.status
   })
   if(!hasCameraPermission){
     await requestPermissionsAsync()
     .then(status => {
       hasCameraPermission = status.status == "granted" ? true : false;
     }).catch((err)=>{
        console.log(err);
     });
   }
 },
 components: { Camera },
};
</script>

<style>
.container {
  flex: 1;
}
.text-color-primary {
  color: blue;
}
</style>