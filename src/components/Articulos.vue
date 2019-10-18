<template>

<section  class="articulos b-flex b-flex-wrap b-flex-center b-flex-center-horizontal">

        <div id="carrito" class="b-flex b-flex-center b-flex-center-horizontal">
            <i class="fas fa-cart-arrow-down"></i>
            <div id="numero-items">
                <p>{{ contador }}</p>
            </div>

        </div>
         
        <article v-for="imagen in temporal" :key="imagen.id">

            <figure class="contenedor-articulo" v-if="mostrar">
     
                    <img :src="require(`@/assets/img/${imagen.url}`)" /> 
                        
                        <figcaption>
                   
                            <h3>{{imagen.nombre}}</h3>
                          

                            <p>+ 0,50 €</p>

                            <button v-on:click="sumar"><i class="fas fa-plus-circle"></i></button>

                        </figcaption>

            </figure>

        </article>     

    </section>
    
</template>

<script>

import { db } from '../db/db.js'; 

export default {
    
    name: 'Articulos',

    props: {
        
        contador: {
            type: Number,
            default: 0,
        },

        isMySiblingClicked : {
            type: String
        },

        miCategoria: {
            type: String,
            default: "Arroces"
        },

    },

  data() {
        return {
            temporal: []
        }
    },

    mounted() {

        //para que se muestren todos los productos
        this.temporal = db;
        console.log(this.miCategoria);
    },

    watch: {

        //cuando mi categoria cambie, la funcion se ejecuta
        miCategoria: function() {
            //console.log(this.miCategoria);
            let self = this;

            // Filtrar
            this.temporal = db.filter(function(producto) {
                return producto.target == self.miCategoria;
            });
        }   
    },

    methods: {
        
        sumar: function () {
            this.contador++ 
        },

        mostrar: function (isMySiblingClicked) {
            isMySiblingClicked == this.imagen.target   
        }

    }

}
</script>


<style scoped>

/*-----seccion articulos----*/

.articulos {

    background-color: rgb(243, 245, 246);
 

}

.articulos h3, .articulos p {

    font-size: 1em;
    padding: 5% 0% 5% 2%;
    color: black;
}

.articulos img {

    width: 100%;
}

.contenedor-articulo {

    position: relative;
    background-color: white;
    margin: 2%;
  
}

.articulos i {

    position: absolute;
    right: 10%;
    bottom: 8%;
    font-size: 2.2em;
}

button{

   border: none;
   font-size: 100%;
   transition: .2s all ease-in-out;
}

button:hover {

    color: rgb(0,207,181);
}

/*------carrito-----*/

#carrito {

    font-size: 1.8em;
    background-color:  rgb(243, 245, 246);
    position: absolute;
    right: 5%;
    top: 31%;
    font-size: 1em;
    z-index: 102;
}

#numero-items {

 
    background-color: orange;
    text-align: center;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    font-size: 1em;
    position: absolute;
    top: -52px;
    right: -10px;

}

#numero-items p {

       color: white;

}


@media screen and (max-width: 980px) {

    #carrito {

        background-color: transparent;
        position: absolute;
        right: 8%;
        top: 23%;
        padding: 10px;

        
    }


     #numero-items {
        position: absolute;
        right: 0px;
        top: -29px;

    }

}
@media screen and (max-width: 768px) {

#carrito {

        background-color: transparent;
        position: fixed;
        right: 15px;
        top: 35px;
        padding: 10px;
        font-size: 1em;

        
    }

    #numero-items {
        position: absolute;
        right: 0px;

    }

    section {

        height: auto;
        margin-top: 10%;
    }
}

</style>

