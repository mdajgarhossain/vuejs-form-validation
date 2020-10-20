<template>
  <div id="app">
    <div class="container">
      <div class="row d-flex justify-content-center my-4 py-2 rounded shadow">
        <div class="col-12">
          <CalculationForm />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CalculationForm from "./components/CalculationForm";
export default {
  name: "App",
  components: {
    CalculationForm,
  },
};
</script>

<style>
html,
#app {
  margin: 0;
  padding: 0;
}
</style>
