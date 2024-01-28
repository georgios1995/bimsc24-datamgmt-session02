<!-- the script is where the js code goes -->
<script setup>
import { ref } from "vue" // you need this to use ref()
let textValue = ref('');
let countValue = ref(0);
let inputValue = ref("");

let newColour = ref("");
let cssSelector = ref("");

let sidebarColour = ref("");
let maincolor = ref("white");

const emits= defineEmits(['updateValue', 'applyColor']);

//My Function
function increase(){
    countValue.value ++;
}

function updateValue(){
    emits('updateValue', inputValue.value);
    textValue.value = " " + textValue.value + inputValue.value;
    inputValue.value = " "
}

function applyColor(){
    const elements = document.querySelectorAll(cssSelector.value);
    elements.forEach(el =>{
        el.style.color = newColour.value;
    })
}
</script>



<!-- the template is where the html code goes -->
<template>

<div id="navbar" class="container">  
        <div id="title">David's bootcamp website website</div>
        
        <div id="logo">
            <img src="/Users/georgiosgrigoriadis/Desktop/cow.jpg" alt="macad cow">
        </div>
    </div>

    <div id="flex">
        <div id="sidebar" class="container" :style="{backgroundColor: sidebarColour}" >
            <strong>Sidebar</strong>
            <input class="block-element" v-model="inputValue">
            <button class="block-element" @click="updateValue">Click me </button>

            <input class="block-element" v-model="componentName">
            <input class="block-element" v-model="newColour">
            <button class="block-element" @click="applyColor">Click to change color</button>
    </div>
        
        <div id="main" class="container" :style="{backgroundColor: maincolor }"> 
        <strong>main</strong>
        {{ textValue }}

           
        </div>
    </div>


</template>



<!-- style is where the css code goes -->
<style scoped>
.block-element{display: block;  /* Makes each element take up the full width */
    margin-top: 10px; /* Adds some space above the button */
    }

html{
    
    background-color: rgb(59, 59, 59); 
    color: white;
}

body{

    margin:0;
}

div{

    /* put the borders in the inside of container */
    box-sizing: border-box;
}

img{

    height: 100%;
    width: auto;

}

#navbar{

    height: 50px;
    border-color: red;
    

}

#flex{
    
    display: flex;
    height: calc(100vh - 50px);
}

#sidebar{
    
    width:30%;
    border-color: blue;

}

#main{
    width:70%;
    border-color: green;
    font-weight: 100;
    font-style: bold;
    font-family: 'Courier New', Courier, monospace;

}

#title{
    width: 70%;
    float:left;
}

#logo{
    width: 30%;
    height: 100%;
    float:right;
    text-align: right;

}

.container{

    border-style: dotted;
    border-width: 1px;

}

</style>