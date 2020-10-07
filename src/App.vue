<template>
  <div id="app">
    <div class="grid">
      <input @keyup.enter="calc()" class="input__result" type="text" v-model="result" placeholder="0">
      <button @click="input(num)" class="cell num" :key = "num" v-for = "num in numbers" > {{ num }}</button>
      <button @click="input(opp)" class="cell opp" :key = "opp" v-for="opp in opperations" >{{ opp }}</button>
      <button @click="reset()" class="cell opp">R</button>
      <button @click="calc()" class="cell opp">=</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      result: '',
      numbers: [1,2,3,4,5,6,7,8,9,0],
      opperations: ['+', '-', '*', '/']
    }
  },
    methods: {
      input: function(char) {
        this.result = this.result.toString();
        this.result+=char;
      },
      reset: function() {
        this.result = "";
      },
      calc: function() {
        this.result = eval(this.result);
      }
    }
  }

</script>

<style>
  #app {
    width: 200px;
    box-shadow: 0 3px 15px gray;
  }

  .input__result {
    width: 200px;
    border: 0;
    color: #243849;
    font-size: 18px;
    padding: 5px;
    text-align: right;
  }

  .grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    width: 100%
  }
  
  .cell {
    flex: 33%;
    height: 50px;
    font-size: 18px;
    border: none;
  }
  
  .num {
    background-color: #243849;
    color: #fff;
    font-weight: 400;
  }

  .cell:hover {
    background-color: #182530;
  }

  .opp {
    background-color: #ff9900;
    color: #243849;
  }

</style>
