<template>
  <div>
    <form @submit.prevent="calculate">
      <input v-model="firstParam" />
      <input v-model="operation" />
      <input v-model="secondParam" />
      <button type="submit">=</button>
    </form>
    {{ result }}
  </div>

</template>

<script>
export default {
  data() {
    return {
      result: 0,
      firstParam: '',
      secondParam: '',
      operation: ''
    }
  },
  methods: {
    calculate() {
      if (isNaN(Number(this.firstParam)) || isNaN(Number(this.secondParam))) {
        this.result = 'Please use numbers'
      }
      switch (this.operation) {
        case '+':
          this.result = parseFloat(this.firstParam) + parseFloat(this.secondParam)
          break;
        case '-':
          this.result = parseFloat(this.firstParam) - parseFloat(this.secondParam)
          break;
        case '*':
          this.result = parseFloat(this.firstParam) * parseFloat(this.secondParam)
          break;
        case '/':
          this.result = parseFloat(this.firstParam) / parseFloat(this.secondParam)
          break;
        default:
          console.log('Unsuported operation')
          break;
      }
    }
  }
}
</script>