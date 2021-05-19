<template>
  <div class="main">
    <div class="calculator">
      <div class="display">{{current || '0'}}</div>
      <div @click="clear" class="btn dot">C</div>
      <div @click="sign" class="btn dot">+/-</div>
      <div @click="percent" class="btn dot">%</div>
      <div @click="divide" class="btn operator">÷</div>
      <div @click="append('7')" class="btn">7</div>
      <div @click="append('8')" class="btn">8</div>
      <div @click="append('9')" class="btn">9</div>
      <div @click="multiply" class="btn operator">×</div>
      <div @click="append('4')" class="btn">4</div>
      <div @click="append('5')" class="btn">5</div>
      <div @click="append('6')" class="btn">6</div>
      <div @click="minus" class="btn operator">-</div>
      <div @click="append('1')" class="btn">1</div>
      <div @click="append('2')" class="btn">2</div>
      <div @click="append('3')" class="btn">3</div>
      <div @click="add" class="btn operator">+</div>
      <div @click="dot" class="btn dot">.</div>
      <div @click="append('0')" class="btn">0</div>
      <div @click="equal" class="btn operator equal">=</div> 
    </div>
    <div><Footer/></div>
  </div>
  
</template>

<script>

import Footer from './Footer'

export default {
  name: 'Calculator',
  components: {
    Footer
  },
  data(){
    return{
      previous: null,
      current: '',
      operator: null,
      operatorClicked: false
    }
  },
  methods:{
    clear(){
      this.current=''
    },
    sign(){
      this.current= this.current.charAt(0) ==='-' ?
        this.current.slice(1) : `-${this.current}`;
    },
    percent(){
      this.current= `${parseFloat(this.current) / 100}`
    },
    append(number){
      if(this.operatorClicked){
        this.current = '';
        this.operatorClicked=false;
      }
      this.current=`${this.current}${number}`;
    },
    dot(){
      if(this.current.indexOf('.')=== -1){
        this.append('.');
      }
    },
    divide(){
      this.operator = (a,b) => a / b;
      this.previous = this.current;
      this.operatorClicked= true;
    },
    multiply(){
      this.operator = (a,b) => a * b;
      this.previous = this.current;
      this.operatorClicked= true;
    },
    minus(){
      this.operator = (a,b) => a - b;
      this.previous = this.current;
      this.operatorClicked= true;
    },
    add(){
      this.operator = (a,b) => a + b;
      this.previous = this.current;
      this.operatorClicked= true;
    },
    equal(){
      this.current= `${this.operator(
        parseFloat(this.current), 
        parseFloat(this.previous)
        )}`;
      this.previous= null;
    }
  }
}
</script>

<style scoped>

  .calculator{
    align-content: center;
    justify-self: center;
    padding: 0 450px;
    width: 450px;
    height: 550px;
    font-size: 40px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);
    margin-bottom: 10px;
  }
  .display{
    grid-column: 1/5 ;
    text-align: right;
    padding: 45px 0;
    height: 75px;
    background-color:lightseagreen;
    color: white;
    border-radius: 10px;
  }
  .equal{
    grid-column: 3/5;
  }
  .btn{
    background-color:cyan;
    border: 1px solid #fff;
    padding: 30px 0;
  }
  .operator{
    background-color:steelblue;
    color: white ;
  }
  .dot{
    background-color:aquamarine;
  }
</style>
