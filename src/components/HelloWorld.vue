<template>
  <div class="container">
    <div id="result"></div>

    <div class="calculate">
      <div class="number">
        <button class="btn" @click="number()" value="1">1</button>
        <button class="btn" @click="number()" value="4">4</button>
        <button class="btn" @click="number()" value="7">7</button>
        <button class="btn btn-warning operator" @click="clean()">AC</button>
      </div>

      <div class="number">
        <button class="btn" @click="number()" value="2">2</button>
        <button class="btn" @click="number()" value="5">5</button>
        <button class="btn" @click="number()" value="8">8</button>
        <button class="btn" @click="number()" value="0">0</button>
      </div>

      <div class="number">
        <button class="btn" @click="number()" value="3">3</button>
        <button class="btn" @click="number()" value="6">6</button>
        <button class="btn" @click="number()" value="9">9</button>
        <button class="btn" @click="number()" value=".">.</button>
      </div>

      <div class="calculator">
        <button class="btn operator" @click="sum()" value="+">+</button>
        <button class="btn operator" @click="except()" value="-">-</button>
        <button class="btn operator" @click="multiply()" value="*">*</button>
        <button class="btn operator" @click="division()" value="/">/</button>
      </div>
      <button class="btn" @click="equal()">=</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      result: "",
    };
  },
  mounted() {
    const numberList = document.querySelectorAll(".number button");
    const result = document.getElementById("result");
    result.innerHTML = this.result;
    for (let i = 0; i < numberList.length; i++) {
      numberList[i].addEventListener("click", (e) => {
        this.result += e.target.value;
        result.innerHTML = this.result;
      });
    }
  },
  methods: {
    clean() {
      const result = document.getElementById("result").innerText;
      this.result = result.substring(0, result.length - result.length);
    },
    equal() {
      const result = document.getElementById("result").innerText;
      this.result = eval(result);
      document.getElementById("result").innerHTML = this.result;
    },
    sum() {
      const result = document.getElementById("result").innerText;
      this.result = result + "+";
      document.getElementById("result").innerHTML = this.result;
    },
    except() {
      const result = document.getElementById("result").innerText;
      this.result = result + "-";
      document.getElementById("result").innerHTML = this.result;
    },
    multiply() {
      const result = document.getElementById("result").innerText;
      this.result = result + "*";
      document.getElementById("result").innerHTML = this.result;
    },
    division() {
      const result = document.getElementById("result").innerText;
      this.result = result + "/";
      document.getElementById("result").innerHTML = this.result;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style>
.container {
  width: 100%;
  margin: 0 auto;
  padding: 0;
  text-align: center;
}

.container #result {
  width: 70%;
  height: 50px;
  line-height: 50px;
  font-size: 30px;
  font-weight: bold;
  text-align: right;
  color: #2c3e50;
  border: 1px solid #2c3e50;
  margin: 0 auto;
  padding: 0;
}

.container .calculate {
  width: 70%;
  margin: 0 auto;
  padding: 0;
  text-align: center;
}

.container .calculate .number button,
.container .calculate .calculator button,
.container button {
  width: 25%;
  height: 50px;
  font-size: 20px;
  border: none;
  border-radius: 0;
  background-color: #2c3e50;
  color: #fff;
  margin: 0;
  padding: 0;
  outline: none;
  cursor: pointer;
}

.container .calculate .number button:hover,
.container .calculate .calculator button:hover,
.container button:hover {
  background-color: #34495e;
}
</style>
