<template>
  <form @submit.prevent="addNote">
    <input class="input" v-model="newNote" placeholder="Add a Note..." />
    <button class="button" type="submit">+</button>
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

<style>
form {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
  padding: 0.5rem;
  border: 1px solid rgb(0, 153, 236);
  border-radius: 4px;
}

  body{
    margin:0px;
    background-color: #000000;
  }
  
  .button {
      border: 2px solid var(--font-color);
      background-color: rgb(0, 153, 236);
      height:3vh;
      padding:1px;
      width:3vw;
      font-size: 1em;
      border-radius: 1rem;
}
.input {
      border: 2px solid var(--font-color);
      height:3vh;
      padding:1px;
      width:73vw;
      font-size: 1em;
     
}
</style>
