<template>
  <form @submit.prevent>
    <head> </head>
    <body>
      <h1>MAKKE Clothing</h1>
      <div class="confirm" v-if="showConfirm">
              <input
          class="Adresse"
          v-model="address"
          type="Adresse"
          placeholder="Adresse"
        />
        <input
         v-model="plz"
         placeholder="PLZ"
         />

         <input
         v-model="ort"
         placeholder="Ort"
         />

         <input
         v-model="stair"
         placeholder="Stiege (optional)"
         />

         <button class ="final" @click="endOrder()" >Zahlungspflichtig bestellen</button>

        </div>


        <div class="end" v-if="showEnd">
        
        <h3> Danke für Ihre Bestellung</h3>
        <h3> Ihr Produkt wird in 7 Tagen unter folgender Adresse ankommen</h3>
        <p> Adresse: {{ address }}</p>
        <p> Postleitzahl : {{ plz }}</p>
        <p> Ort : {{ ort }}</p>
        <p> Stiege : {{stair}}</p>
        </div>

      <div class="shop" v-if="hideProduct">
        <div class="bottoms" v-if="showBottoms">
          <div class="products">
            <img class="imgs" src=../assets/hose.png>
            <h3 class="product-name">Lederhose</h3>

            <button
              @click="hideProducts($event.target.parentElement)"
              class="price"
            >
              150 Euronen
            </button>
            <div class="orders">
              <div class="selection" v-if="showSelection">
                <label for="size">Größe:</label>
                <select v-model="selectedSize" id="size" class="select">
                  <option value="S">S</option>
                  <option value="M">M</option>
                  <option value="L">L</option>
                </select>
              </div>
              <div class="amount" v-if="showAmount">
                <label for="amount">Menge:</label>
                <select v-model="selectedAmount" id="amount" class="select">
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                </select>
              </div>
              <button
                v-if="showOrderButton"
                @click="placeOrder"
                class="order-button"
              >
                Bestellen
              </button>
            </div>
          </div>
          <div class="products">
            <img class="imgs" src=../assets/Badehose.png>
            <h3 class="product-name">Badehose</h3>
            <button
            @click="hideProducts($event.target.parentElement)"
            class="price"
            >
            80 Euronen
            </button>
            <div class="orders">
              <div class="selection" v-if="showSelection">
                <label for="size">Größe:</label>
                <select v-model="selectedSize" id="size" class="select">
                  <option value="S">S</option>
                  <option value="M">M</option>
                  <option value="L">L</option>
                </select>
              </div>
              <div class="amount" v-if="showAmount">
                <label for="amount">Menge:</label>
                <select v-model="selectedAmount" id="amount" class="select">
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                </select>
              </div>
              <button
                v-if="showOrderButton"
                @click="placeOrder"
                class="order-button"
              >
                Bestellen
              </button>
            </div>          
          </div>

          <div class="products">
            <img class="imgs" src=../assets/dior.png>
            <h3 class="product-name">Polar Jort</h3>

            <button
              @click="hideProducts($event.target.parentElement)"
              class="price"
            >
              unbezahlbar
            </button>
            <div class="orders">
              <div class="selection" v-if="showSelection">
                <label for="size">Größe:</label>
                <select v-model="selectedSize" id="size" class="select">
                  <option value="S">S</option>
                  <option value="M">M</option>
                  <option value="L">L</option>
                </select>
              </div>
              <div class="amount" v-if="showAmount">
                <label for="amount">Menge:</label>
                <select v-model="selectedAmount" id="amount" class="select">
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                </select>
              </div>
              <button
                v-if="showOrderButton"
                @click="placeOrder"
                class="order-button"
              >
                Bestellen
              </button>
            </div>
          </div>

          <div class="products">
            <img class="imgs" src=../assets/Pyjama.png>
            <h3 class="product-name">Pyjama</h3>

            <button
              @click="hideProducts($event.target.parentElement)"
              class="price"
            >
              200 Euronen
            </button>
            <div class="orders">
              <div class="selection" v-if="showSelection">
                <label for="size">Größe:</label>
                <select v-model="selectedSize" id="size" class="select">
                  <option value="S">S</option>
                  <option value="M">M</option>
                  <option value="L">L</option>
                </select>
              </div>
              <div class="amount" v-if="showAmount">
                <label for="amount">Menge:</label>
                <select v-model="selectedAmount" id="amount" class="select">
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                </select>
              </div>
              <button
                v-if="showOrderButton"
                @click="placeOrder"
                class="order-button"
              >
                Bestellen
              </button>
            </div>
          </div>
        </div>
        <div class="tops" v-if="showTops">
          <div class="products">
            <img class="imgs" src=../assets/stussy.png>
            <h3 class="product-name">Stüssy Tshirt</h3>

            <button
              @click="hideProducts($event.target.parentElement)"
              class="price"
            >
              40 Euronen
            </button>
            <div class="orders">
              <div class="selection" v-if="showSelection">
                <label for="size">Größe:</label>
                <select v-model="selectedSize" id="size" class="select">
                  <option value="S">S</option>
                  <option value="M">M</option>
                  <option value="L">L</option>
                </select>
              </div>
              <div class="amount" v-if="showAmount">
                <label for="amount">Menge:</label>
                <select v-model="selectedAmount" id="amount" class="select">
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                </select>
              </div>
              <button
                v-if="showOrderButton"
                @click="placeOrder"
                class="order-button"
              >
                Bestellen
              </button>
            </div>
          </div>

          <div class="products">
            <img class="imgs" src=../assets/99based.jpg>
            <h3 class="product-name">99 Based Tshirt</h3>

            <button
              @click="hideProducts($event.target.parentElement)"
              class="price"
            >
              50 Euronen
            </button>
            <div class="orders">
              <div class="selection" v-if="showSelection">
                <label for="size">Größe:</label>
                <select v-model="selectedSize" id="size" class="select">
                  <option value="S">S</option>
                  <option value="M">M</option>
                  <option value="L">L</option>
                </select>
              </div>
              <div class="amount" v-if="showAmount">
                <label for="amount">Menge:</label>
                <select v-model="selectedAmount" id="amount" class="select">
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                </select>
              </div>
              <button
                v-if="showOrderButton"
                @click="placeOrder"
                class="order-button"
              >
                Bestellen
              </button>
            </div>
          </div>

          <div class="products">
            <img class="imgs" src=../assets/basic.png>
            <h3 class="product-name">Basic Tshirt</h3>

            <button
              @click="hideProducts($event.target.parentElement)"
              class="price"
            >
              20 Euronen
            </button>
            <div class="orders">
              <div class="selection" v-if="showSelection">
                <label for="size">Größe:</label>
                <select v-model="selectedSize" id="size" class="select">
                  <option value="S">S</option>
                  <option value="M">M</option>
                  <option value="L">L</option>
                </select>
              </div>
              <div class="amount" v-if="showAmount">
                <label for="amount">Menge:</label>
                <select v-model="selectedAmount" id="amount" class="select"> 
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                </select>
              </div>
              <button
                v-if="showOrderButton"
                @click="placeOrder"
                class="order-button"
              >
                Bestellen
              </button>
            </div>
          </div>

          <div class="products">
            <img class="imgs" src=../assets/zipper.png>
            <h3 class="product-name">99 Based Zipper</h3>

            <button
              @click="hideProducts($event.target.parentElement)"
              class="price"
            >
              70 Euronen
            </button>
            <div class="orders">
              <div class="selection" v-if="showSelection">
                <label for="size">Größe:</label>
                <select v-model="selectedSize" id="size" class="select">
                  <option value="S">S</option>
                  <option value="M">M</option>
                  <option value="L">L</option>
                </select>
              </div>
              <div class="amount" v-if="showAmount">
                <label for="amount">Menge:</label>
                <select v-model="selectedAmount" id="amount" class="select">
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                </select>
              </div>
              <button
                v-if="showOrderButton"
                @click="placeOrder"
                class="order-button"
              >
                Bestellen
              </button>
            </div>
          </div>
        </div>
      </div>

      <div class="Create_Account" v-if="Register">
        <input
          class="First_Name"
          v-model="enteredFirstName"
          type="First_Name"
          placeholder="First Name"
        />
        <input
          class="Last_Name"
          v-model="enteredLastName"
          type="Last_Name"
          placeholder="Last Name"
        />
        <input
          class="Address"
          v-model="address"
          type="Address"
          placeholder="Address"
        />
        <input
          class="email"
          v-model="email"
          type="emailAdress"
          placeholder="e-Mail"
        />
        <input
          class="password"
          v-model="password"
          type="Passwort"
          placeholder="Password"
        />
        <button @click="CreateAccount()" class="Submit">Create Account</button>
      </div>

      <div class="navBar">
        <button @click="showAll" class="All">Shop All</button>
        <button @click="showBottom" class="buttonShop">Bottoms</button>
        <button @click="showTop" class="buttonShop">Tops</button>
        <button @click="showHomei" class="Home">Home</button>
        <button @click="showAboutUs" class="About">About us</button>
        <button @click="Create" class="register">Register Account</button>
      </div>

      <div class="home" v-if="showHome">
        <h2>Home</h2>
        <p>
          Slm bei Makke Clothing olmmmmm. Gönnt bisschen para. Hadi öptüm grsz.
        </p>
        <img class="logo" src="../assets/logo.png" />
      </div>

      <div class="about" v-if="showAbout">
        <h2>Über uns</h2>
        <p>marc alman, berke türk</p>
        <img class="marc" src="../assets/marc.png" />
        <img class="berke" src="../assets/berke.png" />
      </div>
    </body>
  </form>
</template>

<script>
export default {
  emits: ["add-account", "add-order"],
  data() {
    return {
      selectedSize: "",
      password: "",
      address: "",
      plz:"",
      ort:"",
      stair:"",
      showShop: true,
      showBottoms: true,
      showTops: true,
      Register: false,
      enteredFirstName: "",
      Adresse:"",
      enteredLastName: "",
      hideProduct: true,
      email: "",
      showAbout: false,
      showHome: false,
      showSelection: false,
      selectedAmount: "",
      showAboutt: false,
      showOrderButton: false,
      showConfirm: false,
      showEnd:false,
    };
  },
  methods: {
    hideProducts(clickedProduct) {
      const products = document.getElementsByClassName("products");
      for (let i = 0; i < products.length; i++) {
        if (products[i].contains(clickedProduct)) {
          products[i].style.display = "block";
        } else {
          products[i].style.display = "none";
        }
      }
      this.showSelection = true; // Größenauswahl anzeigen
      this.showAmount = true;
      this.showOrderButton = true;
    },
    showBottom() {
      this.showTops = false;
      this.showBottoms = true;
      this.showAbout = false;
      this.showHome = false;
      this.showShop = true;
      this.Register = false;
      this.hideProduct = true;
      this.showAmount = false;
      this.showSelection = false;
      this.showOrderButton = false;
      this.showEnd = false;
    },

    showTop() {
      this.showBottoms = false;
      this.showTops = true;
      this.showAbout = false;
      this.showHome = false;
      this.showShop = true;
      this.Register = false;
      this.hideProduct = true;
      this.showAmount = false;
      this.showSelection = false;
      this.showOrderButton = false;
      this.showEnd = false;
    },

    endOrder(){
      this.$emit(
        "add-order",
        this.plz,
        this.address,
        this.ort,
        this.stair,
        this.selectedSize,
        this.selectedAmount,
      );
      this.showConfirm = false;
      this.showEnd = true;
    },

    showAll() {
      this.showBottoms = true;
      this.showTops = true;
      this.showAbout = false;
      this.showShop = true;
      this.showHome = false;
      this.hideProduct = true;
      this.Register = false;
      this.showAmount = false;
      this.showSelection = false;
      this.showOrderButton = false;
      this.showEnd = false;
    },

    placeOrder() {
      this.hideProduct = false;
      this.showConfirm = true;
    },

    showHomei() {
      this.showAbout = false;
      this.showTops = false;
      this.showBottoms = false;
      this.showHome = true;
      this.hideProduct = true;
      this.Register = false;
      this.showEnd = false;
    },
    showAboutUs() {
      this.showAbout = true;
      this.showTops = false;
      this.showBottoms = false;
      this.showHome = false;
      this.Register = false;
      this.showEnd = false;
    },

    CreateAccount() {
      this.$emit(
        "add-account",
        this.enteredFirstName,
        this.enteredLastName,
        this.password,
        this.address,
        this.email,
      );
      this.showShop = true;
      this.Register = false;
      this.hideProduct = true;
      this.showBottoms = true;
      this.showTops = true;
      this.showAmount = false;
      this.showSelection = false;
      this.showOrderButton = false;
    },
    Create() {
      this.showShop = false;
      this.Register = true;
      this.hideProduct = false;
      this.showAbout = false;
      this.showHome = false;
      this.showEnd = false;
      this.showAmount = false;
      this.showSelection = false;
      this.showOrderButton = false;
    },
  },
};
</script>

<style>
.pricing-button {
  width: 130px;
  height: 100px;
  margin-top: 450px;
  margin-left: 10px;
}
.shop {
  display: flex;
  flex-direction: column !important;
  justify-content: space-evenly !important;
  align-items: center !important;
  margin-left: 10px;
  text-align: center;
  margin-top: -60px;
}
.bottoms,
.tops {
  margin-top: 150px;
  display: flex;
  flex-direction: row !important;
  justify-content: space-evenly !important;
  text-align: center;
}
.marc {
  height: 500px;
  width: 700px;
}
.berke {
  height: 500px;
  width: 500px;
}
.makke {
  display: flex;
  margin-left: 100px;
}
.price {
  font-size: 13px;
  width: 110px;
  height: 50px;
  border: 1px solid black;
  border-radius: 10px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 50px;
}
.product-name {
  text-align: center;
}
.products {
  border: 3px solid black;
  margin-right: 100px;
  width: 200px;
  height: 400px;
  margin-top: -45px;
}
.imgs {
  margin-top: 10px;
  margin-left: auto;
  margin-right: auto;
}
.final{
  margin-left:auto;
  margin-right: auto;
  width:120px;
  border:2px solid black;
  margin-top:50px;
}
.First_Name {
  margin-bottom: 10px;
}
.email {
  margin-top: 10px;
  margin-bottom: 10px;
}
body {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
.Address {
  margin-top: 10px;
}
img {
  height: 160px;
  width: auto;
  position: relative;
  margin-left: 3rem;
}
.logo {
  width: auto;
  height: 200px;
}
.hose1 {
  position: absolute;
  top: 100px;
}
.profil {
  width: 80px;
  height: 80px;
  display: flex;
  align-items: center;
  right: 100px;
}
.Submit {
  height: 50px;
  width: 100px;
  border: 1.6px solid black;
}
.password {
  margin-bottom: 10px;
}
.Create_Account {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
}
.header {
  display: flex;
  justify-content: center;
  flex-direction: column;
  position: relative;
}
.about {
  margin-top: 3rem;
}
.home {
  margin-top: 3rem;
}
.profilee {
  height: 100px;
  width: 100px;
  right: -3000px;
  top: 100px;
}
.selection {
  display: flex;
  justify-content: space-evenly;
  margin-left: auto;
  margin-right: auto;
}
.amount{
  display: flex;
  justify-content: space-evenly;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
}
button {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  margin-left: 10px;
  margin-bottom: 20px;
  width: 70px;
  height: 70px;
  background-color: Transparent;
  margin-top: 10px;
  border: none;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
button:hover {
  background-color: rgb(118, 118, 118);
  text-decoration: solid;
  font-weight: bold;
  color: darkslategray;
}
input {
  height: 30px;
  width: 150px;
}
.select{
  width: 2.5rem;
}
.order-button {
  font-size: 13px;
  width: 205px;
  height: 50px;
  border: 1px solid black;
  border-radius: 5px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  font-weight: bold;
}
.navBar {
  position: fixed;
  font-family: "Didact Gothic";
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: flex-end;
  text-decoration: none;
  position: absolute;
  margin-top: 10px;
  padding-right: 20px;
  border-right: 1.5px solid black;
  border: 1.5px solid black;
  border-bottom: 1.5px solid black;
  top: 20%;
  background-color: rgb(214, 211, 211);
}
h1 {
  align-items: center;
  display: flex;
  justify-content: center;
  margin-top: 1px;
}
h3 {
  align-items: center;
  display: flex;
  justify-content: center;
}
</style>
