<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <ErrorMessage :message="errorMessage" v-if="errorMessage" />
          <NewNote :note="note" @createNote="createNote" />
          <div class="note-header">
            <h1>{{ title }}</h1>
            <div class="icons">
              <svg
                @click="grid = true"
                :class="{ active: grid }"
                xmlns="http://www.w3.org/2000/svg"
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <rect x="3" y="3" width="7" height="7"></rect>
                <rect x="14" y="3" width="7" height="7"></rect>
                <rect x="14" y="14" width="7" height="7"></rect>
                <rect x="3" y="14" width="7" height="7"></rect>
              </svg>
              <svg
                @click="grid = false"
                :class="{ active: !grid }"
                xmlns="http://www.w3.org/2000/svg"
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <line x1="8" y1="6" x2="21" y2="6"></line>
                <line x1="8" y1="12" x2="21" y2="12"></line>
                <line x1="8" y1="18" x2="21" y2="18"></line>
                <line x1="3" y1="6" x2="3" y2="6"></line>
                <line x1="3" y1="12" x2="3" y2="12"></line>
                <line x1="3" y1="18" x2="3" y2="18"></line>
              </svg>
            </div>
          </div>

          <Notes :notes="notes" @removeNote="removeNote" :grid="grid" />
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
      grid: true,
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
