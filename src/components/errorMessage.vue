<template>
  <p class="message">
    {{ message }}
  </p>
</template>

<script>
export default {
  name: 'errorMessage',
  props: {
    message: {
      type: String,
      required: false,
      default: 'Something went wrong...',
    },
  },
};
</script>

<style lang="scss" scoped>
.message {
  margin: 10px 0;
  color: red;
}
</style>
