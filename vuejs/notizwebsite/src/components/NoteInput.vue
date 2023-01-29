<template>
  <form @submit.prevent="addNote">
    <input v-model="newNote" placeholder="Add a Note..." />
    <button type="submit">Add</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      newNote: ''
    }
  },
  methods: {
    addNote() {
      if (!this.newNote) return
      this.$emit('add-Note', this.newNote)
      this.newNote = ''
    }
  }
}
</script>
