<template>
  <div class="new-note">
    <label for="title">Title</label>
    <input id="title" v-model="note.title" type="text" required />
    <label for="desc">Description</label>
    <textarea id="desc" v-model="note.description" required></textarea>
    <button class="btn btn-primary" @click="createNote">New Note</button>
  </div>
</template>

<script>
export default {
  name: "newNote",

  props: {
    note: {
      type: Object,
      required: true,
    },
  },

  methods: {
    createNote() {
      this.$emit("createNote", this.note);
    },
  },
};
</script>

<style lang="scss">
.new-note {
  text-align: center;
}
</style>
