<template>
  <div id="app">
    <ImageCropper src="/profile_sample.jpg"></ImageCropper>
  </div>
</template>

<script>
import ImageCropper from './components/ImageCropper';
export default {
  name: 'App',
  components: {
    ImageCropper
  }
}
</script>

<style>
  .cropper-crop-box, .cropper-view-box {
      border-radius: 50%;
  }
  .cropper-dashed {
    display: none;
  }

  .cropper-line, .cropper-point {
    background-color: transparent; 
  }

  .cropper-center {
    display: none;
  }

  .cropper-view-box {
      outline: 0;
  }
</style>
