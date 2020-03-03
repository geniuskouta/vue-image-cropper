<template>
<div class="img-cropper">
  <div class="img-container">
    <img ref="image" :src="src" />
  </div>
  <img :src="destination" class="img-preview" />
</div>
</template>

<script>
import Cropper from 'cropperjs';

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
    border-radius: 50%;
  }
</style>
