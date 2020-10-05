<template>
  <div>
    <button @click="changeMessage">{{message}}</button>
    <div>
      <button><router-link to="/page2">Go to Page 2</router-link></button>
    </div>
  </div> 
</template>

<script>
export default {
  name: 'Page1',
  data(){
    return {
      message: 'Want to play?'
    }
  },
   methods: {
    changeMessage(){
      if(this.message == 'Want to play?'){
        return this.message = "I am working!"
      }
      return this.message = "Want to play?"
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button{
  margin-top: 20px;
}
</style>
