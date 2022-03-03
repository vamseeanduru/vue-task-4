<template>
  <div id="app">
    <h1>Star Wars Planets</h1>
    <div class="container">
      <button class="btn btn-danger" @click="show = !show">+</button>
      <table
        class="table table-bordered table-hover table-responsive"
        v-if="show"
      >
        <thead class="table-dark">
          <tr>
            <th>Planet Name</th>
            <th>Planet Climate</th>
            <th>Planet Terrain</th>
            <th>Planet Population</th>
          </tr>
        </thead>
        <tbody class="table-primary">
          <tr v-for="planet in planetsList" :key="planet.name">
            <td @click="clicked(planet)">{{ planet.name }}</td>
            <td>{{ planet.climate }}</td>
            <td>{{ planet.terrain }}</td>
            <td>{{ planet.population }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <hello-world v-if="setSelected" :setSelected="setSelected"></hello-world>
    <new-planet v-if="!show" @addPlanetsToTable="showTable"></new-planet>
  </div>
</template>

<script>
import axios from "axios";
import HelloWorld from "./components/HelloWorld.vue";
import NewPlanet from "./components/NewPlanet.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    NewPlanet,
  },
  data() {
    return {
      planetsList: [],
      setSelected: null,
      show: true,
    };
  },
  created() {
    this.getPlanetsList();
  },
  methods: {
    async getPlanetsList() {
      let vm = this;
      vm.planetsList = [];
      await axios
        .get("https://swapi.dev/api/planets")
        .then((res) => {
          vm.planetsList = res.data.results;
        })
        .catch((err) => {
          console.log(err);
        });
    },
    clicked(planet) {
      this.setSelected = planet;
    },
    showTable(data) {
      this.show = true;
      this.planetsList.push(data);
    },
  },
};
</script>

<style lang="scss">
@import "~bootstrap/dist/css/bootstrap.css";
@import "~bootstrap-vue/dist/bootstrap-vue.css";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
input {
  width: 20%;
  font-size: 16px;
  font-size: max(16px, 1em);
  font-family: inherit;
  padding: 0.25em 0.5em;
  background-color: #fff;
  border: 2px solid #000;
  border-radius: 4px;
}
table {
  cursor: pointer;
}

.btn-danger {
  margin-bottom: 20px;
  margin-right: 1000%;
}
</style>
