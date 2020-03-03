<template>
<div>
<div class="img-cropper">
  <div class="img-container">
    <img ref="image" :src="src" />
  </div>
  <img id="cropped-image" :src="destination" class="img-preview" />
</div>
<div class="buttons">
  <button class="c-button">キャンセル</button>
  <button 
    class="c-button"
  >
  <a :href="destination" download="">
  保存
  </a>
  </button>
</div>
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
    /* display: none; */
  }
  .c-button{
    padding: 5px 10px;
    background: transparent;

  }
  .buttons {
    width: 480px;
    display: flex;
    justify-content: flex-end;
  }

  .c-button a{
    color:black;
    text-decoration: none;
  }
</style>
