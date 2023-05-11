<template>

<HelloWorld @add-order ="addOrder"></HelloWorld>
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
  addOrder(address, email, enteredFirstName, enteredLastName, password  ){
    
    fetch(
      "https://semi-a0885-default-rtdb.europe-west1.firebasedatabase.app/order.json",
       //export the Data to Firebase
      {  
        method: "POST",
        headers: {
          "Content-Type":"application/json",
        },
        body: JSON.stringify({
              address: address,
              email: email,
              enteredFirstName: enteredFirstName,
              enteredLastName: enteredLastName,
              password:password
        }),
      }).then ((response) => {
      console.log("response POST request:" , response);
    }).catch((error) => {
      console.log("error: ", error)
    })
    },
  }
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
