<template>
<section>
<new-order @add-order = "addOrder"></new-order>
<ul>
  <my-customers
  v-bind:key="customer"
  v-for="customer in customers"
  :name="customer.name"
  :emailAddress="customer.emailAdress"
  :phone="customer.phone"
  :address="customer.address"
  ></my-customers>
</ul>
</section>
</template>
<script>

import newOrder from "./components/newOrder.vue";


export default {

  name: 'App',
  components: {
    newOrder,
    
  },
  data(){
    return{
      customers: [],
    
    };
  },
  methods:{
    addOrder(address, emailAdress, name, phone  ){
    
  fetch(
    "https://vue-skating-default-rtdb.europe-west1.firebasedatabase.app/order.json",
     //export the Data to Firebase
    {  
      method: "POST",
      headers: {
        "Content-Type":"application/json",
      },
      body: JSON.stringify({
            address: address,
            emailAdress: emailAdress,
            name: name,
            phone: phone,
      }),
    }).then ((response) => {
    console.log("response POST request:" , response);
  }).catch((error) => {
    console.log("error: ", error)
  })
  },
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
