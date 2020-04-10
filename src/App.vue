<template>
    <div class="text-center" id="app">
      <h1>Traductor</h1>
      <h5>Power by Vue.js</h5>
      <app-translate-from v-on:formSubmit="translateText"></app-translate-from>
      <app-translate-out v-text="translatedText"></app-translate-out>
    </div>
</template>

<script>
import TraslateForm from './components/TranslateForm';
import TraslateOutpout from './components/TranslateOutput';
export default {
    name: 'App',
    data(){
      return {
        translatedText: ''
      }
    },
    components: {
      appTranslateFrom: TraslateForm,
      appTranslateOut: TraslateOutpout
    },
    methods: {
      translateText(text, language){
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20191203T043328Z.fbc8aaf8e72730f0.0ab2f027a313aff79b1e9442ca891c6412d45d39&text='+text+'&lang='+language)
        .then((response)=>{
          this.translatedText = response.body.text[0];
        });
      }
    }
}
</script>

<style>
body{
  background: #fefefe;
}


</style>
