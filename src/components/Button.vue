<template>
  <button>
    <slot>Button</slot>
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {

  },

  data: function () {
    return {

      }
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  button {
    border: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
    outline: 0;
    cursor: pointer;
    color: #fff;
    background-color: #27b99a;
    padding: 10px 30px;
    border-radius: 30px;
  }
</style>
