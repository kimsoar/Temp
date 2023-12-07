<template>
  <div class="container">
    <BasicInput v-model="email"/>
    <button @click="testClick">click</button>
    <div style="display: flex; align-items: center;">
      <label class="label-checkbox">
        <input type="checkbox">
        <span>테스트1</span>
    </label>
      <SkewedToggle offText="AND" onText="OR" class="toggle" v-model="skewedToggle"/>
      <label class="label-checkbox">
        <input type="checkbox">
        <span>Checkbox</span>
    </label>
=
      <button>조회</button>
    </div>
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

  label.label-checkbox {
  cursor: pointer;
}


label.label-checkbox input {
  position: absolute;
  top: 0;
  left: 0;
  visibility: hidden;
  pointer-events: none;
}

label.label-checkbox span {
  /* padding: 11px 21px; */
  border: 1px solid #ccc;
  display: inline-block;
  color: #202020;
  border-radius: 6px;
  margin: 7px;
  background: #f5f5f5;
  user-select: none;
}

label.label-checkbox input:checked + span {
  box-shadow: inset 1px 2px 5px #777;
  transform: translateY(1px);
  background: #e5e5e5;
}
}

</style>
