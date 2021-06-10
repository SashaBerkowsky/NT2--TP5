<template>
  <div id="navigator">
    <button id="reset" @click="restart()">
      {{ gane ? "Play again!" : "New Colors" }}
    </button>
    <span id="message"></span>

    <button
      id="easy"
      @click="changeDifficulty('easy')"
      :class="getEstilos(!isHard)"
    >
      easy
    </button>
    <button
      id="hard"
      @click="changeDifficulty('hard')"
      :class="getEstilos(isHard)"
    >
      hard
    </button>
  </div>
</template>

<script lang="js">

  export default  {
    name: 'componentes-navbar',
    props: ["resetAct", "gane"],
    mounted () {
      this.$emit('dificultad', this.isHard)
    },
    data () {
      return {
        isHard: false,
        activeClass: "select",
      }
    },
    methods: {
      changeDifficulty(difficulty){
        this.isHard = difficulty==='hard'
        this.$emit('dificultad', this.isHard)
        this.resetAct()

      },
      restart(){
        this.resetAct()
      },
      getEstilos(isSelected){
        return isSelected ? "selected": "" 
      }
    },
    computed: {
    }
}


</script>

<style scoped lang="css">
#navigator {
  background: #ffffff;
  height: 30px;
  text-align: center;
  margin: 0;
  margin-top: -30px;
}
#message {
  background-color: #ffffff;
  color: black;

  display: inline-block;
  width: 20%;
}

.selected {
  background-color: steelblue;
  color: white;
}
button {
  border: none;
  background-color: white;
  font-family: "Montserrat", "Avenir";
  text-transform: uppercase;
  height: 100%;
  font-weight: 700;
  letter-spacing: 1px;
  color: steelblue;
  transition: all 0.3s;
  outline: none;
}
button:hover {
  color: white;
  background-color: steelblue;
}
</style>
