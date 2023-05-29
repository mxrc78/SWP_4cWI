<template>
    <form @submit.prevent>
      <head>
       
</head>
      <body>
  <h1>MAKKE Clothing</h1>


<div class="shop" v-if="hideProduct">
  <div class="panel">
    <div class="product1">
        <div class ="imggg"><img src=../assets/hose.png>/></div>
        <div class="product-name">
          <h3>Lederhose</h3>
        </div>
        <div class="pricing-button">
          <button class="price">150 Euronen</button>
        </div>
    </div>

    <div class="product2">
      <div class ="imggg"><img src=../assets/Badehose.png>/></div>
      <div class="product-name">
        <h3>Badehose</h3>
      </div>
      <div class="pricing-button">
        <button class="price">200 Euronen</button>
      </div>
    </div>

    <div class="product3">
      <div class ="imggg"><img src=../assets/Elf.png>/></div>
      <div class="product-name">
        <h3>Badehose</h3>
      </div>
      <div class="pricing-button">
        <button class="price">unbezahlbar</button>
      </div>
    </div>

    <div class="product4">
      <div class ="imggg"><img src=../assets/Pyjama.png>/></div>
      <div class="product-name">
        <h3>Badehose</h3>
      </div>
      <div class="pricing-button">
        <button class="price">500 Euronen</button>
      </div>
    </div>
  </div>
</div>
      


  <div v-if="showLogin">
      <button

       
              @click="
                testPassword()
              "

              class="Login"
            >
              Login
            </button>

      <input type="text" v-model="enteredPassword"/>
    </div>



<div class ="Create_Account" v-if="Register">
  <input class ="First_Name" v-model="enteredFirstName" type ="First_Name" placeholder="First Name">
  <input  class ="Last_Name" v-model="enteredLastName" type ="Last_Name" placeholder="Last Name">
  <input class ="Address" v-model="address" type ="Address" placeholder="Address">
  <input  class ="email" v-model="email" type ="emailAdress" placeholder="e-Mail">
  <input  class ="password" v-model="password" type ="Passwort" placeholder="Password">
  <button @click="CreateAccount()" class ="Submit" >Create Account</button>
</div>

<div class ="navBar" v-if="showShop">
  <button class ="All">Shop All</button>
  <button class="d">Shopping cart</button>
  <button class ="Home">Home</button>
  <button class ="About">About us</button>
  <button @click="Create()" class ="register">Register Account</button>
</div>

</body>
</form>
</template>

<script>
export default{

  emits:["add-order"],

data(){
return{
  password: "",
  address: "",
  showShop:true,
  Register:false,
  enteredFirstName: "",
  enteredLastName: "",
  hideProduct:true,

  email: "",
  };
},

methods:{
  testPassword(){
    // eslint-disable-next-line no-cond-assign, no-self-assign
    if (this.enteredPassword ==this.password) {
    this.showShop = !this.showShop
    this.showLogin = !this.showLogin
  }else
    alert("Falsch")
  },
  CreateAccount(){
    this.$emit(
      "add-order",
      this.enteredFirstName,
      this.enteredLastName,
      this.password,
      this.address,
      this.email,
    );
      this.showShop =! this.showShop,
      this.Register =! this.Register
      this.hideProduct =! this.hideProduct
      
  
  },
  Create(){
    this.showShop =! this.showShop
    this.Register =! this.Register
    this.hideProduct =! this.hideProduct
   
  }
}
}
</script>

<style>  
.pricing-button{
  width:130px;
  height:100px;
  margin-top:450px;
  margin-left:10px;
}

.shop{
  display:flex;
  flex-direction: column !important;
  justify-content: space-evenly !important;
  align-items: center !important;
  margin-left:10px;
  text-align: center;
  margin-top:-60px;  
   


}

.panel{

  margin:150px;
  display: flex;
  flex-direction: row !important;
  justify-content: space-evenly !important;
  text-align: center;

}

.price{
  font-size:20px;
  width:200px;
  border:2px solid black;
  border-radius: 10px;
  align-items: center;
}

h3{
  text-align: left;
}
.product-name{
  margin-left: 150px;
  text-align: center;
  position:relative;

}

.product1{
  border: 3px solid black;
  margin-right:100px;
  text-align: left;
  
}

.product2{
  border: 3px solid black;
  margin-right:100px;
  text-align:center;
}

.product3{
  border: 3px solid black;
  margin-right:100px;
}

.product4{
  border: 3px solid black;
  margin-right:100px;
}

.imggg{
  position:absolute;
  padding:50px;
  margin-top:50px;
 
}

.First_Name{
margin-bottom: 10px;
}

.email{
  margin-top:10px;
  margin-bottom:10px;
}

body{
  font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.Address{
  margin-top:10px;
}

img{
  height:160px;
  width:160px;
  position: absolute;
  
}

.logo{
  width:200px;
  height:200pxM
}
.hose1{
  position:absolute;
  top:100px;
}

.profil{
  width: 80px;
  height:80px;
  display:flex;
  align-items: center;
 right:100px;
}

.Submit{
  height:50px;
  width:100px;
  border: 1.6px solid black;
}

.password{
  margin-bottom: 10px;
}

.Create_Account{
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top:20px;

}

.header{
  display:flex;
  justify-content: center;
  flex-direction: column;
  position:relative;
}

.profilee{
  height:100px;
  width:100px;
  right:-3000px;
  top:100px;
}

button{
  display:flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items:center;
  margin-left:10px;
  width:70px;
  height:70px;
  background-color: Transparent;
  margin-top:10px;
  border:none;
  font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; 
}

button:hover{
  background-color:lightgray;
  text-decoration:solid;
  font-weight:bold;
  color:darkslategray;
}

input{
  height: 30px;
  width:150px;
}

.navBar{
  font-family: 'Didact Gothic';
  display:flex;
  align-items:center ;
  flex-direction: column;
  justify-content: flex-end;
  text-decoration: none;
  position:absolute;
  margin-top: 10px;
  padding-right:20px;
  border-right: 1.5px solid black;
  top:20%;
}

h1{
  align-items: center;
  display:flex;
  justify-content: center;
}
</style>
