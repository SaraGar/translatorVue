<template>
  <div id="app">
    <TranslatorForm v-on:formSubmit="textTranslate"></TranslatorForm>
    <TranslatorOutput v-text="translatedText"></TranslatorOutput>
    <!-- <input type='text' v-model="translatedText">-->
  </div>
</template>

<script>
import TranslatorForm from './components/TranslatorForm'
import TranslatorOutput from './components/TranslatorOutput'
export default {
  name: 'App',
  data: function(){
    return {
      translatedText:''
    }
  },
  components: {
    TranslatorForm, 
    TranslatorOutput
  } ,
  methods:{
    textTranslate: function(textToTranslate, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20200402T201750Z.b42852168ab15a31.d59925984681247d364a12112f72819ccd94d59f&text='+textToTranslate+'&lang='+language).then((res)=>{
      this.translatedText = res.body['text'][0];
      });
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
