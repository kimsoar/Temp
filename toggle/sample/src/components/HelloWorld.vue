<template>
  <div class="container">
    <SkewedToggle offText="AND" onText="OR" class="toggle"/>
  </div>
</template>

<script>
import SkewedToggle from './SkewedToggle.vue';
export default {
  name: 'HelloWorld',
  components: {SkewedToggle},
  props: {
    msg: String
  }
}
</script>


<style lang="scss" scoped>
.container {
  background-color: yellow;
  height: 30px;
  /* .toggle{
    width: 50px;
    height: 30px;
  } */
}

</style>
