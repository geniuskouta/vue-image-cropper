<template>
  <div id="app">
    <ImageCropper src="/doge.jpg"></ImageCropper>
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
  body {
    font-family: 'Roboto', sans-serif;
  }
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
