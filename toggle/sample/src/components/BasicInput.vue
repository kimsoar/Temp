<template>
    <input :value="value" ref="input" @input="updated()"/>
  </template>
  
  <script>
  export default {
    props: {
        value: {
            type: String,
            defaults: 'test'
        }
    },
    data () {
      return {
        
      }
    },
    methods: {
        updated() {
            this.$emit('input', this.$refs.input.value)
        }
    }
}
</script>