<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <h1>{{ title }}</h1>
          <ErrorMessage :message="errorMessage" v-if="errorMessage" />
          <NewNote :note="note" @createNote="createNote" />
          <Notes :notes="notes" @removeNote="removeNote" />
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import ErrorMessage from "@/components/ErrorMessage";
import NewNote from "@/components/NewNote";
import Notes from "@/components/Notes.vue";

export default {
  name: "App",
  components: {
    ErrorMessage,
    NewNote,
    Notes,
  },
  data() {
    return {
      title: "Notes App",
      errorMessage: "",
      note: {
        title: "",
        description: "",
      },
      notes: [
        {
          title: "First Note",
          description: "First Description",
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: "Second Note",
          description: "Second Description",
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: "Third Note",
          description: "Third Description",
          date: new Date(Date.now()).toLocaleString(),
        },
      ],
    };
  },
  methods: {
    createNote() {
      let { title, description } = this.note;

      if ((title && description) === "") {
        this.errorMessage = "Title and description are required";
        return;
      }
      this.notes.push({
        title,
        description,
        date: new Date(Date.now()).toLocaleString(),
      });
      this.errorMessage = "";
    },
    removeNote(index) {
      this.notes.splice(index, 1);
    },
  },
};
</script>

<style>
.error-message {
  color: red;
}
</style>
