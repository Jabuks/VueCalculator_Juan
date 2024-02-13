<template>
  <header class="header">Kalkulator Toko Hamster</header>
  <div class="calculator">
    <div class="display">{{current || '0'}}</div>
    <div @click="plus" class="btn-operator">+</div>
    <div @click="min" class="btn-operator">-</div>
    <div @click="times" class="btn-operator">x</div>
    <div @click="divide" class="btn-operator">÷</div>
    <div @click="append('7')" class="btn">7</div>  
    <div @click="append('8')" class="btn">8</div>  
    <div @click="append('9')" class="btn">9</div>  
    <div @click="equals" class="equals"></div>  
    <div @click="append('4')" class="btn">4</div>  
    <div @click="append('5')" class="btn">5</div>  
    <div @click="append('6')" class="btn">6</div>  
    <div @click="equals" class="equals"></div>  
    <div @click="append('1')" class="btn">1</div>  
    <div @click="append('2')" class="btn">2</div>  
    <div @click="append('3')" class="btn">3</div>  
    <div @click="equals" class="equals"></div>  
    <div @click="append('0')" class="btn">0</div>
    <div @click="dot" class="btn">.</div>
    <div @click= "clear" class="btn">AC</div>
    <div @click="equals" class="equals">=</div>
      
    <!-- <h1>Hello nigg</h1> -->
  </div>
</template>

<script>
export default {
  data() {
    return{
      previous: null,
      current:'',
      operator: null,
      operatorClicked: false,
      
    }
  },
  methods: {
    clear(){
      this.current='';
    },
    append(number){
      if (this.operatorClicked) {
        this.current = '';
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
    },
    dot(){
      if (this.current.indexOf('.') === -1){
        this.append('.');
      }
    },
    setPrevious(){
      this.previous = this.current;
      this.operatorClicked = true;
    },
    plus(){
      this.operator = (a,b) => a + b;
      this.setPrevious();
    },
    min(){
      this.operator = (a,b) => a - b;
      this.setPrevious();
    },
    times(){
      this.operator = (a,b) => a * b;
      this.setPrevious();
    },
    divide(){
      this.operator = (a,b) => a / b;
      this.setPrevious();
    },
    equals(){
      this.current = `${this.operator(
        parseFloat(this.current),
        parseFloat (this.previous)
      )}`;
      this.previous = null;
    }
  }
    
  // name: 'SimpleCalculator',
}
</script>

<style scoped>
.calculator{
  font-size: 40px;
  display: grid;
  grid-template-columns: repeat(4,1fr);
  grid-auto-rows: minmax(50px, auto);
}
.header{
  font-weight: 400;
  font-size: 30px;
  height: 80px;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  margin-top: 10px;
  border-radius: 10px;
  width: 100%;
  min-height: 60px;
}

.display {
  grid-column: 1 / 5;
  color: rgb(255, 255, 255);
  background-color: rgb(0, 0, 0);
}

.equals{
  background-color: chocolate;
  /* border: 2px solid; */
}
.btn{
  background-color: rgba(138, 136, 137, 0.555);
  border: 1px solid;
}

.btn-operator{
  background-color: goldenrod;
  color: rgb(0, 0, 0);
  border: 1px solid ;
}


</style>
