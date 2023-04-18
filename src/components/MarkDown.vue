<template>
  <h1>Markdown App</h1>
  <div class="con">
    <div class="f-d">
      <textarea :value="text" @input="btnText"></textarea>
    </div>

    <div class="s-d" v-html="markedText">
      
    </div>
  </div>
</template>


<script>
import { marked } from 'marked';
export default{
  name: "MarkDown",
  data(){
    return{
      text: '',
      timeout: ''
    }
  },
  computed:{
    markedText(){
      return marked(this.text);
    }
  },
  methods:{
    btnText(event){
      clearTimeout(this.timeout)
      this.timeout = setTimeout(()=>{
        this.text = event.target.value
      }, 2000)

      // console.log(event.target.value)
    }
  }

}
</script>


<style scoped>
h1 {
  text-align: center;
}
.con {
  display: flex;
  margin-top: 2vh;
}

.s-d {
  border: 2px solid black;
  background-color: gray;
  height: 100vh;
}

.f-d{
  width: 50%;
  border: 2px solid black;
  margin-left: 4vw;
}
.s-d {
  width: 50%;
  margin-right: 4vw;
}

textarea {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  overflow: visible;
}
</style>
