  <template>
   <div class="form-area">
    <h1>Calculator</h1>
    <div class = "input">     
          <input class = "input-types" type="text" v-model="number" placeholder="Enter Calculation">
          <simple-button
          @add-calc="add"
          @minus-calc="minus"
          @multiply-calc="multiply"
          @divide-calc="divide"
          @equals-calc="equals"
          ></simple-button>
    </div>
  </div>
  </template>
  <script>
   
import SimpleButton from './SimpleButton.vue'
  export default {
    name: 'App',
    components: {
        SimpleButton
    },

    data(){
      return{
      number1: "",
      number2: "",
      number: "",
      operator: "",
      result: "",
      }
     },        
        methods: {
          add(){
            this.number1 = this.number;
            this.number = "";
            this.operator = "+";
          },
          minus(){
            this.number1 = this.number;
            this.number = "";
            this.operator = "-";
          },
          multiply(){
            this.number1 = this.number;
            this.number = "";
            this.operator = "*";
          },
          divide(){
            this.number1 = this.number;
            this.number = "";
            this.operator = "/";
          },
          equals(){
            this.number2 = this.number;
        
            switch(this.operator){
            case "+":
              this.result = parseInt(this.number1) + parseInt(this.number2); 
              console.log(this.result);
              break;
            case "-":
              this.result = parseInt(this.number1) - parseInt(this.number2);
              console.log(this.result);
              break;
            case "*":
              this.result = parseInt(this.number1) * parseInt(this.number2);
              console.log(this.result);
              break;
            case "/":
              this.result = parseInt(this.number1) / parseInt(this.number2);
              console.log(this.result);
              break;
          }
            this.number = this.result;
        }
       },
      }
  </script>
  <style>

.input-types{
    height: 50px;
    width: 600px;
    margin-left:auto;
    margin-right:auto;
}
h1{
    padding-top:20px;
}
div.form-area{
    background-color: grey;
    height: 400px;
    width: 700px;
    margin-left: 300px;
    margin-top: 150px;
    box-shadow:5px;
    border-radius:10px;
    box-shadow:10px 10px 10px 10px rgba(0, 0, 0, 0.2);
}
body{
    background-color:orangered;
}
  </style>