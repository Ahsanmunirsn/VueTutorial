<template>
  <div>
    <h1>Speed Typer</h1>
    <p>Your Score: 
      {{keywords.filter(keyword => keyword.correct).length}} / {{keywords.length}}</p>
    <p>
      <span 
        :class="{
          correct: keyword.correct,
          wrong: keyword.wrong,
          pending: keyword.pending 
          }"
        :key="keyword.text" v-for="keyword in keywords">
        {{ keyword.text }}{{' '}}</span>
    </p>
    <input type="text" :value="inputValue" 
    @keyup.space="processInput($event)">
    
  </div>
</template>

<script>

const defaultKeywords = ['template', 'data', 'javascript', 'angular', 'vue', 'react', 'python', 'movie', 'gym', 'football', 'software', 'engineer', 'university']
.map(keyword =>{
  return {
    text: keyword,
    correct: false,
    wrong: false,
    pending: true
  }
})
     

export default {
  data(){
    return {
      inputValue: "",
      index: 0,
      keywords: defaultKeywords,
     };
  },
  methods: {
      processInput(event){  
      const value = event.target.value.trim();

      if(value === "") {
        return;
      }
      if(this.keywords[this.index].text === value){
        //correct answer
        this.keywords[this.index].correct = true;
        this.keywords[this.index].wrong = false;
        this.keywords[this.index].pending = false;
      } else{
        //wrong answer
        this.keywords[this.index].correct = false;
        this.keywords[this.index].wrong = true;
        this.keywords[this.index].pending = false;
      }

      this.inputValue = "";
      this.index++;
    },
  },
}; 
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.pending {
  font-weight: bold;
}
.correct{
  font-weight: bold;
  color: green;
}
.wrong{
  font-weight: bold;
  color: red;
}

</style>
