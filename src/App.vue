<template>
  <div id="app">
      <div class="box_calc">
          <div class="title_calc">
              {{display}}
          </div>
          <div class="main_calc">
               <button class="clear" @click="clear">C</button>
               <button class="right_side" @click="plus">+</button>
               <button class="right_side" @click="minus">-</button>
               <button class="right_side" @click="zarp">*</button>
                <button @click="add(6)">6</button> 
               <button @click="add(7)">7</button>
               <button @click="add(9)">9</button>
               <button class="right_side" @click="dictive">%</button>
                <button @click="add(4)">4</button>
               <button @click="add(5)">5</button>
               <button @click="add(6)">6</button>
               <button @click="addPoint('.')" class="right_side">.</button>
                <button @click="add(3)">3</button>
               <button @click="add(2)">2</button>
               <button @click="add(1)">1</button>
               <button @click="add(0)" class="right_side">0</button>
               <button class="clear" @click="equal">Equal</button>

          </div>
      </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      display:"",
      operator:null,
      perv:null,
      operClick:false,
    }
  },

  methods: {
    clear(){
      this.display = ""
    },
    add(e){
      if (this.operClick) {
        this.display="";
        this.operClick=false;
      }
      this.display += e;
    },

    addPoint(){
      if (this.display.indexOf('.' ) == -1) {
        this.display += "."
      }
    },

    setporve(){
      this.perv = this.display;
      this.operClick=true;
    },

    plus(){
        this.operator = (a,b) => a + b;
        this.setporve();
    },

    minus(){
        this.operator = (a,b) => a - b;
        this.setporve();
    },

    dictive(){
        this.operator = (a,b) => a / b;
        this.setporve();

    },

    zarp(){
        this.operator = (a,b) => a * b;
        this.setporve();

    },

    equal(){
      this.display= `${this.operator(parseFloat(this.perv) , parseFloat(this.display))}`

    }


  },
}


</script>

<style>
*{
  margin: 0; padding: 0;
}
#app {
  height: 100vh;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex; justify-content: center; align-items: center;
  background-color: #2c3e50;
}
.box_calc{
  width: 40%; height: 40%;
}
.title_calc{
  height: 20%;
  background-color: #2c3e50;
  color: #fff;
  display: flex; justify-content: start; align-items: center;
  padding-left: 1rem;
  font-size: 1.2rem;
  font-weight: bolder;
}
.main_calc{
  height: 80%;
  display: flex; justify-content: space-around;
  align-items: center;
  flex-wrap: wrap;
}
.main_calc button{
  width: 6.9rem; height: 2rem;
  font-weight: bolder;
}
.clear{
  background-color: rgb(138, 19, 19);
}
.right_side{
  background-color: rgb(231, 171, 59);
  border-radius: .5rem;
}
</style>
