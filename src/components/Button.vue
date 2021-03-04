<template>
  <button @click="onClick()" >{{ btntext }}</button>
</template>

<script>
export default {
  name: "Button",
  props: {
    btntext: String,
  },
  methods : {
      onClick() {
          this.$emit('btn-click')
      }
  }
};
</script>