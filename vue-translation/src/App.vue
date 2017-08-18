<template>
  <div id="app">
    <h2>在线翻译</h2>
    <h6 class="text-muted">Design by Xin Shunning </h6>
    <h6 class="text-muted">github - https://github.com/a77321a</h6>
    <h5 class="">简单 /易用 /便捷</h5>
      <translateForm v-on:formSubmit="translateText"></translateForm>
      <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/translateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  data:function(){
    return {
      translatedText:""
    }
  },
  components: {
      TranslateForm,TranslateOutput
  },
  methods:{
    translateText:function(text,language){
     this.$http.get(`https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170818T044802Z.f2e9a9872bf16590.894ce13439f049018f7314c023eef13f1c5eaa23&lang=${language}&text=${text}`).then((response)=>{
        this.translatedText=response.body.text[0];
     })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
