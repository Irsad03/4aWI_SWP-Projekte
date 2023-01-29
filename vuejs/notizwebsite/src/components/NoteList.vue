<template>
  <ul>
    <li v-for="note in notes" :key="note.id">
      {{ note.name }}
<button @click="removeNote(note.id)">X</button>
</li>

  </ul>
</template>
<script>
export default {
  props: {
    notes: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    removeNote(id) {
      console.log(id);
      this.$emit('remove-note', id)
    }
  }
}
</script>

