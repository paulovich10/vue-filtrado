<template>
  <div id="app">

    <header>
        <Cabecera/>
       <Navegacion @showcat="showCategories"/>
        <div id="barra-separacion"></div>
    </header>

    <Articulos :mi-categoria="category"/>

  </div>
</template>

<script>

import Cabecera from './components/Cabecera.vue';
import Navegacion from './components/Navegacion.vue';
import Articulos from './components/Articulos.vue'


export default {
  
  name: 'app',
  
  components: {
    Cabecera,
    Navegacion,
    Articulos
  },

    data() {
        return {

            category: ""
        }
    },

    methods: {

        // Capturamos el evento 
        showCategories(category) {
            this.category = category;
        } 

    }

}
</script>

<style>

  * {
    margin: 0px;
    padding: 0px;
    box-sizing: border-box;
}

.b-flex {

    display: flex;
} 

.b-flex-row {

    flex-direction: row;
}

.b-flex-center {

    align-items: center;
}

.b-flex-center-horizontal {

   justify-content: center;
}

.b-flex-wrap {

    flex-wrap: wrap;
}

h3,p{

    font-family: 'Roboto Condensed', sans-serif;
    
}

a {
    font-family: 'Roboto', sans-serif;
    text-decoration: none;
    color: rgba(0,0,0,.6);
    padding: 10px 20px;
    margin: 0 1%;
    border-radius: 30px;
    transition: .7s cubic-bezier(0.075, 0.82, 0.165, 1);
    
    
}

a:hover {

    border: 1px solid rgb(0,207,181);
    color: rgb(0,207,181);
    transform: scale(1.1);

}

#barra-separacion {

    width: 100%;
    background: linear-gradient(to top, rgba(0,0,0,.3), rgba(0,0,0,.1));
    height: 20px;
}



</style>
