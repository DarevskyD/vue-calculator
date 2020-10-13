<template>
  <div class="calculator">
    <div class="display">{{current || '0'}}</div>  
    <div @click="clear" class="btn operator-horiz">AC</div>
    <div class="btn operator-horiz">+/-</div>
    <div class="btn operator-horiz">%</div>
    <div class="btn operator">÷</div>
    <div class="btn">7</div>
    <div class="btn">8</div>
    <div class="btn">9</div>
    <div class="btn operator">x</div>
    <div class="btn">4</div>  
    <div class="btn">5</div>
    <div class="btn">6</div>
    <div class="btn operator">-</div>
    <div class="btn">1</div>
    <div class="btn">2</div>
    <div class="btn">3</div>
    <div class="btn operator">+</div>
    <div class="btn zero">0</div> 
    <div class="btn">.</div>
    <div class="btn operator">=</div>   
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: '',
    }
  },
  methods: {
    clear() {
      this.current = '';
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calculator {
  width: 400px;
  margin: 0 auto;
  font-size: 30px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}

.display {
  grid-column: 1/5;
  background-color: #1a1a1a;
  color: white; 
}

.zero {
  grid-column: 1/3;
}

.btn {
  background-color: #d1d2d5;
  border: 1px solid #a8a9aa;
  color:#909192;
}

.operator {
  background-color: #39b31b;
  color: white;
}

.operator-horiz {
  background-color: #c7c9cb;  
}

</style>
