<template>
  <img :src="image" alt="" v-drag class="face">
</template>

<script>
import $ from 'jquery';
import "jquery-ui/ui/widgets/draggable"; // this works directly, but need to include each widget separately
import "jquery-ui-touch-punch-c/jquery.ui.touch-punch.min.js";

  export default {
    props: ['image'],
    directives: {
      drag: {
        bind(el, binding, vnode) {
          $(document).ready(function() {
            $(el).draggable({
              // snap: true,
              stack: ".face",
              distance: 0,});
          });
        }
      }
    }
  }
</script>

<style lang="scss">
.face {
  border-radius: 10px;
  box-shadow: 0 0 5px #999;
  margin: 10px;
  width: 200px;height: 200px;
  object-fit: cover;
}
</style>
