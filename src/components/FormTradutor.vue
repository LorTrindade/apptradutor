<template>
  <div class="row" id="FormTradutor">
    <div class="col-md-6 col-md-offset-3">
     <form id="tradForm" class="form-inline well" v-on:submit="formSubmit">
        <input class="form-control" type="text" v-model="textToTranslate" placeholder="Digite uma palavra">
        <select class="form-control" v-model="language">
            <option value="pt">Português</option>
            <option value="es">Espanhol</option>
            <option value="fr">Francês</option>
            <option value="it">Italiano</option>
        </select>
        <br>
        <br>
        <input class="btn btn-primary" type="submit" value="Traduzir">
     </form>
    </div>
  </div>
</template>

<script>

export default {
  name: 'formTradutor',
  data() {
      return {
          textToTranslate: '',
          language: ''
      }
  },
  created() {
      this.language = 'pt';
  },
  methods: {
      formSubmit(e){
          this.$emit('formSubmit', this.textToTranslate, this.language);
          e.preventDefault();
      }
  }
}
</script>

<style>

#tradForm {
    border-radius: 10px;
    border: 1px #CCC solid;
}
</style>
