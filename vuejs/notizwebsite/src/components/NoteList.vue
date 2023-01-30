<template>
  <ul>
    <li v-for="note in notes" :key="note.id">
      {{ note.name }}
<button class="btn" @click="removeNote(note.id)">x</button>
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

<style>
li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
  padding: 0.5rem;
  border: 1px solid rgb(0, 153, 236);
  border-radius: 4px;
  color:aliceblue;
}


.btn {
      border: 2px solid var(--font-color);
      background-color: rgb(0, 153, 236);
      height:3vh;
      padding:1px;
      width:3vw;
      text-align:center;
      font-size:1em;
      font-weight: 10;
      border-radius: 1rem;
}
</style>