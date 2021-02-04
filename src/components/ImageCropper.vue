<template>
<div>
<div class="img-cropper">
  <div class="img-container">
    <img ref="image" :src="src" />
  </div>
  <img id="cropped-image" :src="destination" class="img-preview" />
</div>
<div class="buttons">
  <a :href="destination" download="">
  保存
  </a>
</div>
</div>
</template>

<script>
import Cropper from 'cropperjs';
/*
* https://github.com/fengyuanchen/cropperjs
*/

export default {
  name: 'ImageCropper',
  props: {
    src: {
      type: String
    }
  },
  data() {
    return {
      cropper: {},
      destination: {},
      image: {}
    }
  },
  mounted() {
    this.image = this.$refs.image;
    this.cropper = new Cropper(this.image, {
      zoomable: false,
      scalable: false,
      aspectRatio: 1,
      crop: () => {
        const canvas = this.cropper.getCroppedCanvas();
        this.destination = canvas.toDataURL("image/png");
      } 
    });
  }
}
</script>

<style scoped>
  .img-cropper{
    display: flex;
    justify-content: flex-start;
  }
  .img-container{
    width: 480px;
    height: 480px;
  }
  .img-preview{
    width: 200px;
    height: 200px;
    margin: 20px;
  }
</style>
