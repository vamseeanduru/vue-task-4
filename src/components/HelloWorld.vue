<template>
  <div class="container">
    <table class="table table-bordered table-hover table-responsive">
      <thead class="table-dark">
        <tr>
          <th>Planet Name</th>
          <th>Planet Climate</th>
          <th>Planet Terrain</th>
          <th>Planet Population</th>
        </tr>
      </thead>
      <tbody class="table-success">
        <tr>
          <td>{{ setSelected.name }}</td>
          <td>{{ setSelected.climate }}</td>
          <td>{{ setSelected.terrain }}</td>
          <td>{{ setSelected.population }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    setSelected: Object,
  },
  created() {
    console.log(this.setSelected);
  },
};
</script>

<style>
@import "~bootstrap/dist/css/bootstrap.css";
@import "~bootstrap-vue/dist/bootstrap-vue.css";
h1 {
  font-size: 50px;
}
</style>
