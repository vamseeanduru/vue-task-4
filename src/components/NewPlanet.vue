<template>
  <div class="container">
    <div>
      <b-form-input
        type="text"
        v-model="addPlanets.name"
        placeholder="Planet Name"
      ></b-form-input>
      <br />
      <b-form-input
        type="text"
        v-model="addPlanets.climate"
        placeholder="Planet Climate"
      ></b-form-input>
      <br />
      <b-form-input
        type="text"
        v-model="addPlanets.terrain"
        placeholder="Planet Terrain"
      ></b-form-input>
      <br />
      <b-form-input
        type="text"
        v-model="addPlanets.population"
        placeholder="Planet Population"
      ></b-form-input>
      <br />
      <button @click="addPlanetsToTable" class="btn btn-primary">Submit</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "NewPlanet",
  data() {
    return {
      addPlanets: {
        name: null,
        climate: null,
        terrain: null,
        population: null,
      },
    };
  },
  methods: {
    addPlanetsToTable() {
      this.$emit("addPlanetsToTable", this.addPlanets);
    },
  },
};
</script>

<style scoped>
@import "~bootstrap/dist/css/bootstrap.css";
@import "~bootstrap-vue/dist/bootstrap-vue.css";
input {
  margin-left: 40%;
  width: 20%;
  font-size: 16px;
  font-size: max(16px, 1em);
  font-family: inherit;
  padding: 0.25em 0.5em;
  background-color: #fff;
  border: 2px solid #000;
  border-radius: 4px;
}
</style>
