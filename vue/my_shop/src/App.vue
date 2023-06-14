app.vue
<template>
  <HelloWorld 
    @add-account ="addAccount"
    @add-order ="addOrder"
  ></HelloWorld>
</template>
  
  <script>
  import HelloWorld from './components/HelloWorld.vue'
  
  export default {
    name: 'App',
    components: {
      HelloWorld
    },
    data(){
      return{
        customers:[],
      };
    },
    methods:{
    addAccount(enteredFirstName, enteredLastName, address, email, password) {
      fetch(
        "https://finito-9f20a-default-rtdb.europe-west1.firebasedatabase.app/account.json",
         //export the Data to Firebase
        {  
          method: "POST",
          headers: {
            "Content-Type":"application/json",
          },
          body: JSON.stringify({
            enteredFirstName: enteredFirstName,
            enteredLastName: enteredLastName,
            address: email,
            email: password,
            password: address,
          }),
        }
      )
        .then ((response) => {
          console.log("response POST request:" , response);
        })
        .catch((error) => {
        console.log("error: ", error);
        });
      },

      addOrder(address, plz, ort, stair, selectedSize, selectedAmount) {
      fetch(
        "https://finito-9f20a-default-rtdb.europe-west1.firebasedatabase.app/details.json",
         //export the Data to Firebase
        {  
          method: "POST",
          headers: {
            "Content-Type":"application/json",
          },
          body: JSON.stringify({
            address: plz,
            plz: address,
            ort: ort,
            stair: stair,
            selectedSize: selectedSize,
            selectedAmount: selectedAmount,
          }),
        }
      )
        .then ((response) => {
          console.log("response POST request:" , response);
        })
        .catch((error) => {
        console.log("error: ", error);
        });
      }
    },
  };
  </script>
  
  <style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  </style>