<template>
<div class="fundo">
        <h1> jpfranca </h1>
</div>
    <div class="calculadora">
        <h1> Calculator</h1>
        <div class="display">
          <div class="formula" v-cloak>{{ formula }}</div>
          <div class="result" v-cloak>{{ result }}</div>
        </div>
        <table>
            <tr>
                <td> <button class="button" @click="cleanAll()">AC</button></td>
                <td> <button class="button" @click="drop()">C</button></td>
                <td> <button class="button" @click="toggle()">±</button></td>
                <td> <button class="button" @click="square()">√</button></td>
                
            </tr>
            <tr>
                <td> <button class="button" @click="operate(7)">7</button></td>
                <td> <button class="button" @click="operate(8)">8</button></td>
                <td> <button class="button" @click="operate(9)">9</button></td>
                <td> <button class="button" @click="operate('/')">/</button></td>
                
            </tr>
            <tr>
                <td> <button class="button" @click="operate(4)">4</button></td>
                <td> <button class="button" @click="operate(5)">5</button></td>
                <td> <button class="button" @click="operate(6)">6</button></td>
                <td> <button class="button" @click="operate('*')">*</button></td>
                
            </tr>
            <tr>
                <td> <button class="button" @click="operate(1)">1</button></td>
                <td> <button class="button" @click="operate(2)">2</button></td>
                <td> <button class="button" @click="operate(3)">3</button></td>
                <td> <button class="button" @click="operate('+')">+</button></td> 
            </tr>
            <tr>
                <td colspan="2"> <button style="width: 102px;" class="button" @click="operate(0)">0</button></td>
                <td> <button class="button" @click="operate('.')">.</button></td>   
                <td> <button class="button" @click="operate('-')">-</button></td>
            </tr> 
            <tr>
            <td colspan="4"> <button style="width: 204px;" class="button" @click="equal()">=</button></td>
            </tr> 
        </table>
    </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
     formula :"",
     result : 0 
    }
  },

  methods:{
    operate(element){
      console.log("operate..");
      this.formula +=element;
    },

    equal(){
      console.log("equal..");
      this.result = eval(this.formula);
    },

    cleanAll(){
      console.log("cleanAll..");
      this.formula = "";
      this.result = 0;
    },

    drop(){
        console.log("drop..");
        this.formula = this.formula.slice(0, -1);
    },

    square(){
        console.log("square..");
        console.log(eval(this.formula));
        eval(this.formula)<0? this.formula = "Can not suqre the negative value" : this.result=Math.sqrt(eval(this.formula));
   },


   toggle(){
        console.log("toggle.."); 


        this.formula===""||this.formula.endsWith("+"||"-"||"*"||"/"||"%")? {} :  this.formula.startsWith("-")?this.formula = Math.abs(eval(this.formula)).toString(): this.formula="-("+this.formula+")";
        this.equal();
   }

 }
}
</script>


<style scoped>
*{
            margin: 0;
            padding: 0;
        }
        .fundo{
            background-image: linear-gradient(0deg,black,rgb(59, 59, 59));
            height: 100ch;
            font-family: Arial, Helvetica, sans-serif;
            color: white;
            text-align: center;
        }
        .calculadora{
            position: absolute;
            text-align: center;
            top: 50%;
            left: 50%;
            transform: translate(-50%,-40%);
            color: white;
            border-radius: 10px;
            padding: 10px;
            background-color: rgba(94, 8, 8, 0.9)
            
        }
       .button{
           width: 50px;
           height: 50px;
           font-size: 25px;
           cursor: pointer;
           margin: 3;
           background-color: rgb(10, 10, 10);
           border: none;
           color: white;
       }
       .button:hover{
           background-color: black;           
       }
       .result{
           background-color: white;
           width: 200px;
           height: 20px;
           margin: 2px;
           color: black;
           text-align: right;
           padding: 3px;
           border-radius: 5px;
       }
       .formula{
           background-color: white;
           width: 200px;
           height: 20px;
           margin: 2px;
           color: black;
           text-align: right;
           padding: 3px;
           border-radius: 5px;
       }
</style>
