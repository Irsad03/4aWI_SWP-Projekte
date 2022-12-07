<template>
  <div class="wrapper">
      <div class="main">
          <h1>Simple Calculator</h1>
          <input v-model="aktuellerWert"/>
          <div class="row">
              <simple-button class="btn" beschriftung="+" @calculate="calculate"></simple-button>
              <simple-button class="btn" beschriftung="-" @calculate="calculate"></simple-button>
              <simple-button class="btn" beschriftung="*" @calculate="calculate"></simple-button>
              <simple-button class="btn" beschriftung="/" @calculate="calculate"></simple-button>
          </div>
          <simple-button id="large" class="btn" beschriftung="=" @calculate="calculate"></simple-button>
     </div>
  </div>
</template>

<script>
import SimpleButton from "./SimpleButton.vue";

export default {
  name: 'TheCalculator',
  components: {
      SimpleButton
  },
  data() {
      return {
          vorherierWert: 0,
          aktuellerWert: "",
          vorherigerOperator: ""
      }
  },
  methods: { /*hier hat michael blessing ein klein wenig geholfen*/
      calculate(beschriftung) {
          if(beschriftung === "+" | beschriftung === "-" | beschriftung === "*" | beschriftung === "/") {
              this.vorherierWert = parseInt(this.aktuellerWert);
              this.aktuellerWert = "";
              this.vorherigerOperator = beschriftung;
          } else if(beschriftung === "=") {
              if(this.vorherigerOperator === "+") {
                  this.aktuellerWert = this.vorherierWert + parseInt(this.aktuellerWert);
              } else if(this.vorherigerOperator === "-") {
                  this.aktuellerWert = this.vorherierWert - parseInt(this.aktuellerWert);
              } else if(this.vorherigerOperator === "*") {
                  this.aktuellerWert = this.vorherierWert * parseInt(this.aktuellerWert);
              } else if(this.vorherigerOperator === "/") {
                  this.aktuellerWert = this.vorherierWert / parseInt(this.aktuellerWert);
              }
          } else {
              console.log("Falsche Beschriftung");
          }
      }
  }
  
}
</script>


<style scoped>
  body, * {
      --font-color: #b1149e;
       font-family: 'Roboto', sans-serif;
       background-color: #000000;
       margin: 0px;
       padding-top: 60px;

  }
  .wrapper {
      padding:0px;
      margin:0px;
      height:100vh;
      width:100vw;
      display:flex;
      flex-direction:column;
      align-items: center;
      background-color:#000000;
  }
  .main {
      width: 80vw;
      padding:20px;

  }
  .main > h1 {
      text-align: center;
      font-weight: 600;
      font-size:3em;
      color: var(--font-color);
  }
  input {
      width:79.7vw;
      height:10vh;
      padding:0px;
      margin-bottom:20px;
      border: 2px solid var(--font-color);
      font-size:2em;
      background-color: white;
  }
  .row {
      display:flex;
      flex-direction: row;
      gap:30px;
  }
  .btn {
      border: 2px solid var(--font-color);
      background: #b1149e;
      height:10vh;
      padding:20px;
      width:20vw;
      text-align:center;
      font-size:2em;
      font-weight: 600;
      border-radius: 1rem;
  }
  #large {
      margin-top:20px;
      width:80vw;
      border: 2px solid var(--font-color);
      height:10vh;
      background: #b1149e;
      padding:20px;
      text-align:center;
      font-size:2em;
      font-weight: 600;
      border-radius:1rem;
  }
.btn:hover, #large:hover {
    transition: 0.3s;
    background-color: #7b00ff;
    color: #b1149e;
    border: 2px solid #b1149e;
}

</style>