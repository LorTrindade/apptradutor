<template>
  <div id="app" class="text-center">
    <h1>App Tradutor</h1>
    <h5>powered by LorTrindade.</h5>
    <FormTradutor v-on:formSubmit="translateText"></FormTradutor>
    <TradutorOutput v-text="translatedText"></TradutorOutput>
  </div>
</template>

<script>
import FormTradutor from './components/FormTradutor';
import TradutorOutput from './components/TradutorOutput';

export default {
  name: 'App',
  components: {
    FormTradutor,
    TradutorOutput
  },
  data: function() {
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText:function(text, language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180329T124349Z.791353ddb5a0dfcd.c6eac2e3509328a328dfd831935e88060d6e47c0&lang='+language+'&text='+text)
      .then((response) => {
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>
body {
  background: #FFC0CB;
}
</style>
