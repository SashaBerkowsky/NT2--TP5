<template>
  <div id="app">
    <div id="header" :style="{ background: headerColor }">
      <h1>
        The Great <br />
        <span id="colorDisplay">{{ pickedColor }}</span>
        <br />
        Guessing Game
      </h1>
    </div>
    <Navbar
      @dificultad="leerDificultad($event)"
      :resetAct="restart"
      :gane="gane"
      :inProgress="inProgress"
    />
    <Game
      :isHard="isHard"
      @gane="leerGane($event)"
      @pickedColor="leerColor($event)"
      @restart="leerRestart($event)"
    />
  </div>
</template>

<script>
import Navbar from "./componentes/Navbar.vue";
import Game from "./componentes/Game.vue";

export default {
  name: "App",
  mounted() {},
  data() {
    return {
      isHard: true,
      pickedColor: "RGB",
      restart: "",
      gane: false,
      headerColor: "steelblue",
      inProgress: false,
    };
  },
  methods: {
    leerDificultad(dificultad) {
      this.isHard = dificultad;
    },
    leerColor(pickedColor) {
      this.pickedColor = pickedColor;
    },
    leerRestart(restart) {
      this.restart = restart;
    },
    leerGane(gane) {
      this.gane = gane;
      this.headerColor = this.gane ? this.pickedColor : "steelblue";
    },
  },
  components: {
    Navbar,
    Game,
  },
};
</script>

<style>
#app {
  background: #232323;
  margin: 0;
  font-family: "Montserrat", "Avenir";
}
#header {
  transition: all 0.3s;
  text-transform: uppercase;
  text-align: center;
  margin: 0;
  color: white;
}
#colorDisplay {
  font-size: 200%;
}
</style>
