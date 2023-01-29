<template>
  <div ckass>
    <div>
      <h1>Notizen</h1>
      <NoteInput @add-note="addNote" />
      <NoteList :notes="notes" @remove-note="removeNote" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import NoteInput from "./components/NoteInput.vue";
import NoteList from "./components/NoteList.vue";

export default {
  components: {
    NoteInput,
    NoteList,
  },

  data() {
    return {
      notes: [],
    };
  },
  created() {
    this.fetchNotes();
  },
  methods: {
    async fetchNotes() {
      try {
        const response = await axios.get(
          "https://notizen-be627-default-rtdb.europe-west1.firebasedatabase.app/notes.json"
        );
        if (!response.data) {
          this.results = [];
          return;
        }
        let newData = Object.entries(response.data);
        for (let i = 0; i < newData.length; i++) {
          this.notes.push({ id: newData[i][0], name: newData[i][1].name });
        }
      } catch (error) {
        console.error(error);
      }
    },

    async addNote(note) {
      try {
        const response = await axios.post(
          "https://notizen-be627-default-rtdb.europe-west1.firebasedatabase.app/notes.json",
          { name: note }
        );
        this.notes.push({ id: response.data.name, name: note });
      } catch (error) {
        console.error(error);
      }
    },
    async removeNote(id) {
      try {
        await axios.delete(
          `https://notizen-be627-default-rtdb.europe-west1.firebasedatabase.app/notes/${id}.json`
        );
        console.log(id);
        this.notes = this.notes.filter((note) => note.id !== id);
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>
