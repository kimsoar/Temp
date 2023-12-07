<template>
  <div class="container">
    <SkewedToggle offText="OFF" onText="ON" class="toggle" v-model="skewedToggle"/>
    <BasicInput v-model="email"/>
    <button @click="testClick">click</button>
  </div>
</template>

<script>
import SkewedToggle from './SkewedToggle.vue';
import BasicInput from './BasicInput.vue';
export default {
  name: 'HelloWorld',
  components: {SkewedToggle, BasicInput},
  props: {
    msg: String
  },
  data() {
    return {
      email: "hello@email.com",
      skewedToggle: false,
    }
  },
  methods: {
    testClick() {
      console.log(this.skewedToggle);
    }
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
