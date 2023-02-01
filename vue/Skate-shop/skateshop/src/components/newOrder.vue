<template>
  <form @submit.prevent>
    <div class="hide" v-if="hideOrder">
      <!-- Show Products from the beginning-->
      <h1>ALL PRODUCTS</h1>
      <div class="omg">
        <div class="panel pricing-table">
          <div class="pricing-plan">
            <div class="img"><img src="../assets/yo.png" /></div>
            <h2 class="pricing-header">gx1000 Skate-Deck</h2>
            <ul class="pricing-features">
              <li class="pricing-features-item">
                made out of sustainable wood
              </li>
            </ul>
            <span class="pricing-price">75€</span>
            <button class="count" @click="enteredAmount1 += 1">+</button>
            <button class="minus" @click="(enteredAmount1 -= 1), amountDecks()">
              -
            </button>
            <h1>Amount: {{ enteredAmount1 }}</h1>
            <button
              id="test"
              @click="
                showInput = !showInput;
                hideOrder = !hideOrder;
              "
              class="pricing-button"
            >
              BUY
            </button>
          </div>
        </div>
        <div class="hide" v-if="hideOrder">
          <div class="panel pricing-table">
            <div class="pricing-plan">
              <div class="img"><img src="../assets/biggg.png" /></div>

              <h2 class="pricing-header">Polar Big Boy Pants</h2>
              <ul class="pricing-features">
                <li class="pricing-features-item">Size L</li>
              </ul>
              <span class="pricing-price">130€</span>
              <button class="count" @click="enteredAmount2 += 1">+</button>
              <button
                class="minus"
                @click="(enteredAmount2 -= 1), amountPants()"
              >
                -
              </button>
              <h1>Amount: {{ enteredAmount2 }}</h1>
              <button
                id="test"
                @click="
                  showInput = !showInput;
                  hideOrder = !hideOrder;
                "
                class="pricing-button"
              >
                BUY
              </button>
            </div>
          </div>
        </div>
        <div class="hide" v-if="hideOrder">
          <div class="panel pricing-table">
            <div class="pricing-plan">
              <div class="img"><img src="../assets/proo.png" /></div>
              <h2 class="pricing-header">Tyshawn Pro Shoe</h2>
              <ul class="pricing-features">
                <li class="pricing-features-item">20 % Sale!</li>
              </ul>
              <span class="pricing-price"><div class="sale">80 €</div></span>
              <button class="amount" @click="enteredAmount3 += 1">+</button>
              <button
                class="minus"
                @click="(enteredAmount3 -= 1), amountShoe()"
              >
                -
              </button>
              <h1>Amount: {{ enteredAmount3 }}</h1>
              <button
                id="test"
                @click="
                  showInput = !showInput;
                  hideOrder = !hideOrder;
                "
                class="pricing-button"
              >
                BUY
              </button>
              <!--hide all Products but show the Input types-->
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="input" v-if="showInput">
      <!--show Input Types after clicking on button-->
      <div class="videoh">
        <video autoplay loop muted plays-inline class="videoh">
          <source src="../assets/finallyswp.mp4" />
        </video>
      </div>
      <div class="text">
        <h4>Please fill in the information below</h4>
      </div>
      <div>
        <input type="text" v-model="enteredName" placeholder="Name" />
      </div>
      <div>
        <input type="text" v-model="enteredMail" placeholder="eMail" />
      </div>
      <div>
        <input type="text" v-model="enteredPhone" placeholder="Phone" />
      </div>
      <div>
        <input type="text" v-model="enteredAddress" placeholder="Address" />
      </div>
      <button
        @click="
          takeOrder(),
            (thankYou = !thankYou),
            hideOrder,
            (showInput = !showInput)
        "
      >
        Order
      </button>
      <!--show thank you site, close the input and Order-->
    </div>

    <div class="yk" v-if="thankYou">
      <div class="videoh">
        <video autoplay loop muted plays-inline class="videoh">
          <source src="../assets/finallyswp.mp4" />
        </video>
      </div>
      <div class="thanks">
        <h1>Thank you for your Order! &#128151;</h1>
        <h1>Shipment Details:</h1>
        <p>Your Address: {{ enteredAddress }}</p>
        <p>Name: {{ enteredName }}</p>
        <p>Phone Number: {{ enteredPhone }}</p>
        <p>eMail: {{ enteredMail }}</p>
        <p>Amount of Deck: {{ enteredAmount1 }} {{}}</p>
        <p>Amount of Jeans : {{ enteredAmount2 }}</p>
        <p>Amount of Shoes: {{ enteredAmount3 }}</p>
        <h1>If there are any issues contact us via emailAddress</h1>
        <p>eMail: marc.madlener@student.htldornbirn.at</p>
      </div>
    </div>
  </form>
</template>
<script>
export default {
  // props können als array angegeben werden
  emits: ["add-order"],
  data() {
    return {
      showInput: false,
      hideOrder: true,
      thankYou: false,
      enteredAddress: "",
      enteredName: "",
      enteredMail: "",
      enteredPhone: "",
      enteredAmount1: 0,
      enteredAmount2: 0,
      enteredAmount3: 0,
    };
  },

  methods: {
    takeOrder() {
      this.$emit(
        "add-order",
        this.enteredMail,
        this.enteredPhone,
        this.enteredName,
        this.enteredAddress
      );
    },

    amountShoe() {
      if (this.enteredAmount3 < 0) {
        this.enteredAmount3 = 0;
        alert("Amount must be higher than 0");
      }
    },

    amountPants() {
      if (this.enteredAmount2 < 0) {
        this.enteredAmount2 = 0;
        alert("Amount must be higher than 0");
      }
    },
    amountDecks() {
      if (this.enteredAmount1 < 0) {
        this.enteredAmount1 = 0;
        alert("Amount must be higher than 0");
      }
    },
  },
};
</script>

<style>
.videoh {
  position: absolute;
  z-index: -1;
  right: 0;
  bottom: 0;
  top: 0;
  left: 0;
  height: 1000px;
}

@media (min-aspect-ratio: 16/9) {
  .videoh {
    width: 110%;
    height: auto;
  }
}

@media (max-aspect-ratio: 16/9) {
  .videoh {
    width: 110%;
    height: auto;
  }
}

h1 {
  align-items: center;
  text-align: center;
}

h2 {
  color: black;
  font-size: 1vw;
}

h4{
    color: aliceblue;
}
.text {
  margin-top: 200px;
}

.amount {
  margin-top: -100px;
}
div {
  margin-bottom: 10px;
}
.thanks {
  color: aliceblue;
}

button {
  background-color: black;
  color: white;
  width: 350px;
  padding-top: 10px;
  padding-bottom: 10px;
  margin-top: 15px;
}
h3 {
  color: black;
  font-size: 1vw;
}

p {
  color: aliceblue;
}
.amount {
  height: 50px;
  width: 50px;
  margin-right: 20px;
  background-color: transparent;
  color: black;
}

@media screen and (max-width: 900px) {
  .omg {
    display: flex;
    flex-direction: column !important;
    justify-content: center !important;
    align-items: center !important;
   
  }
  h1 {
    text-align: center;
  }
}

.minus {
  height: 50px;
  width: 50px;
  background-color: transparent;
  color: black;
}

.count {
  height: 50px;
  width: 50px;
  margin-right: 20px;
  background-color: transparent;
  color: black;
}

.count:hover {
  background-color: rgb(67, 69, 71);
  color: white;
}

.minus:hover {
  background-color: rgb(67, 69, 71);
  color: white;
}

.amount:hover {
  background-color: rgb(67, 69, 71);
  color: white;
}

button:hover {
  background-color: rgb(67, 69, 71);
  color: white;
}

input {
  width: 350px;
  height: 20px;
  padding-top: 5px;
  padding-bottom: 5px;
  padding-left: 10px;
}

input::placeholder {
  font-weight: bold;
  color: rgb(64, 60, 60);
}

img {
  height: 200px;
  margin-top: 19px;
}
.omg {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
}

.line {
  font-size: 15px;
  text-decoration: line-through;
  color: rgb(248, 112, 112);
  line-height: 1em;
}
.panel {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  margin: 10px;
  padding: 2rem;
  background-color: transparent;
  border: 5px solid black;
  border-radius: 8px;
  text-align: center;
  font-family: Arial;
  height: 700px;
  width: 310px;
}
.pricing-panel:nth-child(2) {
  border-right-width: 1px;
  border-right-style: groove;
  border-right-color: rgb(46, 124, 134);
}

.pricing-plan {
  height: 200px;
}
.pricing-features-item {
  text-align: center;
  font-size: 10px;
  border-bottom-style: groove;
  border-width: 1px;
  border-color: rgb(28, 29, 30);
  color: rgb(28, 29, 30);
  justify-content: center;
  list-style-type: "";
  padding: 10px;
  font-weight: bold;
  text-transform: uppercase;
  font-family: sans-serif;
  padding: 12px 0px 12px 0px;
}
.pricing-header {
  font-size: 25px;
  margin-top: 35px;
  margin-bottom: 60px;
  color: rgb(28, 29, 30);
  font-weight: bold;
  text-transform: uppercase;
}
ul {
  display: inline-block;
  margin: 0;
  padding: 0;
  zoom: 1;
  display: inline;
}
.pricing-price {
  display: flex;
  text-align: center;
  font-size: 30px;
  justify-content: center;
  color: rgb(28, 29, 30);
  margin-bottom: 25px;
  margin-top: 25px;
  font-weight: bold;
  text-transform: uppercase;
  height: 45px;
}
.pricing-features-item:nth-child(1) {
  border-top-style: groove;
  border-top-width: 1px;
  border-top-color: rgb(28, 29, 30);
}
.pricing-img {
  width: 50%;
}
.pricing-button {
  border-style: groove;
  border-color: rgb(28, 29, 30);
  background-color: transparent;
  border-width: 1px;
  padding: 10px 30px 10px 30px;
  text-decoration: none;
  border-radius: 10px;
  color: rgb(28, 29, 30);
  font-weight: bold;
  text-transform: uppercase;
  width: 200px;
}

.pricing-button:hover {
  background-color: rgb(28, 29, 30);
  color: white;
}

.is-featured {
  border-style: groove;
  border-color: rgb(28, 29, 30);
  border-width: 1px;
  padding: 10px 30px 10px 30px;
  text-decoration: none;
  border-radius: 10px;
  color: rgb(28, 29, 30);
  font-weight: bold;
  text-transform: uppercase;
}
.pricing-plan:nth-child(2) {
  border-right-width: 1px;
  border-right-style: groove;
  border-right-color: rgb(28, 29, 30);
  border-left-width: 1px;
  border-left-style: groove;
  border-left-color: rgb(28, 29, 30);
  padding-left: 85px;
  padding-right: 85px;
  margin-right: 85px;
  margin-left: 85px;
}

body {
  background-color:blanchedalmond;
}
</style>
