<template>
  <button @click="calculate">
    {{operator}}
  </button>
</template>

<script>


export default {
  emits: ['calculate'],
  name:'SimpleButton',
  props: {
    operator: String
  },
  data() {
    return [];
  },
  methods: {
    calculate() {
      this.$emit('calculate', this.operator);
    }
  }
}
</script>