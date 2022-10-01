<script>
    export default{
        data: () => ({
            contador:500,
        }),
        methods:{
            saludar(){
                console.log("Hola 10A");
            },
            incrementar(){
                this.contador++;
            },
            decrementar(){
                this.contador--;
            },
            reset(){
                this.contador = 500;
            }
        }
    };



</script>



<template>


    <img src="./assets/logo.svg" alt="Logo VUE" width="125" height="125">
     
     <div class="container">
    <small>
        <h1>Hola desde Vue.js 3</h1>
    </small>
    <h2>Jesus Hilario Juarez Ortiz</h2>
    <br>
    <br>
    <br>
    <h3>Contador {{ contador }}</h3>
    <button @click="incrementar()">+1</button> 
    <button @click="decrementar()">-1</button>
    <button @click="reset()">Reset</button>
     </div>

</template>

<style>

    .container{
        text-align: center;
    }

    small{
        color: #666;
    }
    h1{
        font-weight: bolder;
    }

    h2{
        color: blue;
    }

    h3{
        font-size: 2rem;
    }
    button{
        cursor: pointer;
        font-size: 1.5rem;
        margin: 0px 8px;
    }

</style>










