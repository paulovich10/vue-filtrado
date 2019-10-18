<template>
  <div class="m-container-cabecera">

        <img id="logo" src="../assets/img/logo.svg" alt="logo apeteat">

        <div class="b-flex b-flex-row desaparece-movil">

            <div class="m-precio">

                <p>Menú completo 9 €</p>

            </div>
            <div class="m-precio">

                <p>Medio menú 6 €</p>

            </div>


        </div>

    </div>
</template>

<script>
export default {
  name: 'Cabacera',
  props: {
    msg: String
  }
}
</script>


<style scoped>

.m-container-cabecera img{

    width: 180px;
    margin-top: 2%;
    margin-left: 2%;
}

.m-container-cabecera p {

    font-weight: 700;
}

.m-precio {

    background-color: rgba(0,0,0,.1);
    margin: 2%;
    border-radius: 10px;
  
}

.m-precio p {

    padding: 1.5rem;
    font-size: .9rem;
}

@media screen and (max-width: 768px) {


    /*-----cabecera invertida-----*/


    header {

        display: flex;
        flex-flow: column-reverse;
      
    }

    #logo {
        width: 120px;
       margin-left: 30%;
       position: fixed;
       z-index: 9999;

    }

    .desaparece-movil {

        display: none;
    }

}

</style>
