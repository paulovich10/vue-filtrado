<template>

 <div class="navegacion b-flex b-flex-row">

       <i v-on:click="abrir" id="barras" class="fas fa-bars"></i>
 
        <nav v-bind:class="{ abierto: isAbierto }" class="l-nav b-flex b-flex-center">
            <a v-on:click="capturar" href="#">Entrantes</a>
            <a v-on:click="capturar" href="#">De cuchara</a>
            <a v-on:click="capturar" href="#">Pastas</a>
            <a v-on:click="capturar" href="#">Arroces y cereales</a>
            <a v-on:click="capturar" href="#">Ensaladas y zumos</a>
        </nav>

       
    </div>

</template>

<script>
export default {
  name: 'Navegacion',
  props: {
      isAbierto: false
  },
  methods: {

      abrir: function() {
          this.isAbierto = !this.isAbierto
      },

      capturar: function(e) {
        this.$emit('showcat', e.target.innerText);
        
      }
  }
}
</script>

<style scoped>

.l-nav {

    height: 80px;
    padding-left: 2%;
    background-color: rgb(243, 245, 246);
    width: 100%;

}

.fa-bars {

    position: absolute;
    top: 0;
    left: 0;
    visibility: hidden;
    font-size: 2.5em;
    padding-top: 10px;
    padding-left:10px;
}



@media screen and (max-width: 768px) {

/*-----navegacion-----*/
    
    .fa-bars {
        visibility: visible;
        z-index: 99;
        position: fixed;
        background-color:rgb(255, 255, 255);
        width: 100%;
        padding-bottom: 2%;
        z-index: 100;

    }

    .l-nav {

        flex-direction: column;
        align-items: center;
        justify-content: center;
        transform: translateX(-100%);
        position: absolute;
        background-color: rgba(255 255 255);
        z-index: 98;
        transition: .5s all ease-in-out;
    }

    .l-nav.abierto {
        transform: translateX(0);
        height: 100vh;
        position: fixed;
        
    }

    
    nav a {

        font-size: 1.3em;
    }
}

</style>