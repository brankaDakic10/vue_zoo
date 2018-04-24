<template>
  <div >
      <button :disabled="isDisabled" @click="disableButton"> click me</button>
      <button @click="confirm">{{ label }}</button>
  </div>
</template>

<script>
export default {
  data(){
      return {
          isDisabled: false,
          label: 'Confirm'
      }
  },
  methods:{
      disableButton(){
          this.isDisabled = true
          setTimeout(()=> {
              this.isDisabled = false
          }, 3000)
      },
      confirm(){
        if (this.label === 'are u sure?'){
          this.label = "Success"
        }
        else{
          this.label = "are u sure?"
        }
        if (this.timeout){
          clearTimeout(this.timeout)
          this.timeout = null
          return
        }
        if (this.label === 'Success'){
        this.label.setTimeout(()=>{
          this.label = "confirm"
        }, 3000)
      }}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>