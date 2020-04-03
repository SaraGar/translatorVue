<template>
  <div id="translatorForm">
   <form v-on:submit="submitForm">
    <textarea v-model="textToTranslate" rows=10 placeholder ='Text to translate...'></textarea><br>
    <select v-model="language">
        <option value="en">Inglés</option>
        <option value="pt">Portugués</option>
        <option value="it">Italiano</option>
        <option value="fr">Francés</option>
        <option value="nl">Alemán</option>
        <option value="ru">Ruso</option>
        <option value="ja">Japonés</option>
    </select>
    <input type='submit' value='Traducir!'/><br>
    <br><i>(Powered by <a href="http://translate.yandex.com">Yandex.Translate</a>)</i><br><br>
   </form>
  </div>
</template>

<script>
export default {
  name: 'TranslatorForm',
  data: function(){
      return{
        textToTranslate: "",
        language: "en"
        
      }
  },
  methods:{
      submitForm:function(e){
         /*  alert(this.textToTranslate); */
         this.$emit("formSubmit", this.textToTranslate, this.language);
          e.preventDefault();
      }
  }
}
</script>

<style>
</style>
