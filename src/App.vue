<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <h1>{{ title }}</h1>
          <div class="error-message" v-if="errorMessage">
            {{ errorMessage }}
          </div>
          <div class="new-note">
            <input v-model="note.title" type="text" required />
            <textarea v-model="note.description" required></textarea>
            <button @click="createNote">New Note</button>
          </div>
          <div class="notes">
            <div class="note" v-for="(note, index) in notes" ::key="index">
              <div class="note-header">
                <p>{{ note.title }}</p>
              </div>
              <div class="note-body">
                <p>{{ note.description }}</p>
                <span>{{ note.date }}</span>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      title: 'Notes App',
      errorMessage: '',
      note: {
        title: '',
        description: '',
      },
      notes: [
        {
          title: 'First Note',
          description: 'First Description',
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: 'Second Note',
          description: 'Second Description',
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: 'Third Note',
          description: 'Third Description',
          date: new Date(Date.now()).toLocaleString(),
        },
      ],
    };
  },
  methods: {
    createNote() {
      let { title, description } = this.note;

      if ((title && description) === '') {
        this.errorMessage = 'Title and description are required';
        return;
      }
      this.notes.push({
        title,
        description,
        date: new Date(Date.now()).toLocaleString(),
      });
      this.errorMessage = '';
    },
  },
};
</script>

<style>
.error-message {
  color: red;
}
</style>
