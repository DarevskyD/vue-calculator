<template>
  <div class="calculator">
    <div class="display">{{current || '0'}}</div>  
    <div @click="clear" class="btn operator-horiz">AC</div>
    <div @click="mark" class="btn operator-horiz">+/-</div>
    <div @click="percent" class="btn operator-horiz">%</div>
    <div @click="divide" class="btn operator">÷</div>
    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="multiply" class="btn operator">x</div>
    <div @click="append('4')" class="btn">4</div>  
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="minus" class="btn operator">-</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="plus" class="btn operator">+</div>
    <div @click="append('0')" class="btn zero">0</div> 
    <div @click="dot" class="btn">.</div>
    <div @click="equal" class="btn operator">=</div>   
  </div>
</template>

<script>
export default {
  data() {
    return {
      previous: null,
      current: '',
      operator: null,
      operatorClicked: false,
    }
  },
  methods: {
    clear() {
      this.current = '';
    },
    mark() {
      this.current = this.current.charAt(0) === '-' ? this.current.slice(1) : `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(num) {
      if(this.operatorClicked) {
        this.current = '';
        this.operatorClicked = false;
      }
      this.current = `${this.current}${num}`;
    },
    dot() {
      if(this.current.indexOf('.') === -1) {
        this.append('.');
      }
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },
    multiply() {
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    minus() {
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },
    plus() {
      this.operator = (a, b) => a + b;
      this.setPrevious();
    },
    equal() {
      this.current = `${this.operator(
        parseFloat(this.previous),
        parseFloat(this.current)
      )}`;
      this.previous = null;
    }
  }
}
</script>

<style scoped>
.calculator {
  width: 340px;  
  margin: 0 auto;
  font-size: 30px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(70px, auto);
  box-shadow: 0 0 10px #909192;
}

.display {
  grid-column: 1/5;
  background-color: #1a1a1a;
  color: white;
  text-align: right;
  padding: 20px;
  font-size: 50px;  
}

.zero {
  grid-column: 1/3;
}

.btn {
  background-color: #d1d2d5;
  border: 1px solid #a8a9aa;
  color:#909192;
  cursor: pointer;
}

.operator {
  background-color: #39b31b;
  color: white;
}

.operator-horiz {
  background-color: #c7c9cb;  
}
</style>
