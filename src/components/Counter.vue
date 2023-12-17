<template>
    <h2>{{customTitle}}</h2>
    <p>{{counter}} <sup>2</sup> = {{ squareCounter }}</p>
    <div>
        <!-- <button v-on:click="decrease">-1</button>
        <button v-on:click="increase">+1</button> -->
        <button @click="decrease">-1</button>
        <button @click="increase">+1</button>
    </div>
</template>

<script>
export default {
    //Como obtener las properties
    // props:['title'],
    props:{
        title:String,
        start:{
            type: Number,
            // default:1,
            validator(value){
                return value>=0
            }
            // required:true
        }
    },
    //Todo lo que agregue dentro de counter es reactivo
    data(){
        return {
            counter:this.start
        }
    },
    methods:{
        getSquareValue(){
            return this.counter * this.counter
        },
        increase(){
            this.counter++
        },
        decrease(){
            this.counter--
        }
    },
    //Se guardan en cache a diferencia de methods
    computed:{
        squareCounter(){
            return this.counter * this.counter
        },
        customTitle(){
            return this.title || 'Counter'
        }
    }
}
</script>

<style>
    button{
        background-color: #54bb87;
        border-radius:  5px;
        border: 1px solid white;
        color: whitesmoke;
        cursor: pointer;
        margin: 0 5px;
        padding: 5px 15px;
        transition: 0.3s ease-in-out;
    }
    button:hover{
        background-color: #5aa67b;
        transition: 0.3s ease-in-out;
    }
</style>