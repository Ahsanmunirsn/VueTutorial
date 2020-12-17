<template>
  <div>
    <h1>Typing Speed</h1>
    <p>{{keywords.join(' | ') }}</p>
    <input :value="inputValue" @keyup.space="processInput($event)">
    
  </div>
</template>

<script>
export default {
  data(){
    return {
      inputValue: "",
      index: 0,
      keywords: [],
    };
  },
  methods: {
    processInput(event){
      const value = event.target.value;
      this.keywords[this.index] = value;
      this.inputValue = value;
      this.index++;
    }
  }
  
}; 
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
