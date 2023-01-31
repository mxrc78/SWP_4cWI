<template>
        <div class = "buttons">
            <button @click="plus" class ="single-button" id="plus" type="text">+</button>
            <button @click = "minus" class ="single-button"  id = "minus" type="text">-</button>
            <button @click="mal" class ="single-button"  id = "mal" type="text">*</button>
            <button @click="teilen" class ="single-button"  id = "teilen" type="text">/</button>
        </div>
        <div class="special">
            <button @click="gleich" class ="single-button-is" type="text">=</button>        
        </div>
  </template>

  <script>
    export default{
        emits: ['add-Calc'],
        methods:{
           plus(){
                this.$emit("add-Calc");
            },
            minus(){
                this.$emit("minus-Calc");
            },
            mal(){
                this.$emit("multiply-Calc");
            },
            teilen(){
                this.$emit("divide-Calc");
            },
            gleich(){
                this.$emit("equals-Calc");
            }
        },
    }
</script>
<style>

.buttons{
    display:flex;
    flex-direction: row;
    justify-content: space-evenly;
}
.single-button{
    padding:20px 20px 20px 20px;
    margin-top:40px;
    background-color:orange;
    border: 1px solid black;   
    height: 50px;
    width:60px;
    box-shadow:10px 10px 10px 10px rgba(0, 0, 0, 0.2);
}
.special{
    display:flex;
    justify-content: center;
    flex-direction: column;
    text-align:center;
}

.single-button-is{
    background-color:orange;
    display:flex;
    flex-direction: column;
    justify-content: center;
    margin-left: 40px;
    margin-right: 30px;
    margin-top: 40px;
    height: 50px;
    width: 600px;
    padding-left: 300px;
    box-shadow:10px 10px 10px 10px rgba(0, 0, 0, 0.2);
}
.single-button:hover{
    background-color:orangered;
}
.single-button-is:hover{
    background-color:orangered;
}
body{
    background-color:orangered;
}
</style>