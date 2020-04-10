<template>
    <div class="row" id="translateForm">
        <div class="col-md-6 col-md-offset-3">        
            <form id="transForm" class="form-inline well" v-on:submit="formSubmit">
                <input class="form-control" type="text" v-model="textToTranslate" placeholder="Introduce una palabra">
                <select class="form-control" v-model="language">
                    <option value="en">Ingles</option>
                    <option value="es">Español</option>
                    <option value="it">Italiano</option>
                    <option value="fr">Frances</option>
                    <option value="ru">Ruso</option>
                    <option value="he">Hebreo</option>
                    <option value="la">Latin</option>
                    <option value="zh">Chino</option>
                    <option value="ja">Japones</option>
                    <option value="ca">Catalan</option>
                </select>
                <input class="btn btn-primary" type="submit" value="Traducir">
            </form>
        </div>
    </div>
</template>

<script>
export default {
    name: 'translateform',
    data(){
        return {
            textToTranslate: '',
            language: ''
        }
    },
    created() {
        this.language = 'en';
    },
    methods: {
        formSubmit(e){     
            this.$emit('formSubmit', this.textToTranslate, this.language)       
            e.preventDefault();
        }
    },

  
}
</script>

<style>
#transForm {
    border-radius: 10px;
    border: 1px #ccc solid;    
    -webkit-box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.75);
    -moz-box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.75);
    box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.75);
    
}

.btn-primary {
    background-color: #2d8adc!important;
    /*border-color: #2d8adc;*/
    border: none;
    padding: 7px 25px;
    font-size: 15px;
}
.btn-primary:hover {
    background-color:#2196F3!important;
}



</style>
