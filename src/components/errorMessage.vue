<template>
  <div class="error-message">
    {{ message }}
  </div>
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

<style>
.error-message {
  margin: 10px 0;
  color: red;
}
</style>
