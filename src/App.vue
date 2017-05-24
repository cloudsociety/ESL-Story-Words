<template>
  <div id="grid">
    <appDragItem v-for="(image, index) in faces"
          :image="image"
          :key="index"></appDragItem>
  </div>
</template>

<script>
import _ from 'lodash';

import DragItem from './DragItem.vue';

// import gulp-generated image data
import {ImagesMixin} from './ImagesMixin.js';

export default {
  computed: {
    faces(){
      return _.shuffle(this.images).map((cube) => {
          return _.shuffle(cube).pop();
        }
      );
    }
  },
  mixins: [ImagesMixin], // add the images object to `data`
  components: {
    appDragItem: DragItem
  }
}
</script>

<style lang="scss">
body {
  background-color: #ddd;
}
#grid {
  margin: 0 auto;padding: 0;
  width: 660px;
}
</style>
