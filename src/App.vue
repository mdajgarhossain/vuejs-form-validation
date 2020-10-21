<template>
  <div id="app">
    <div class="container">
      <div class="row d-flex justify-content-center my-4 py-2 rounded shadow">
        <div class="col-12">
          <VuelidateFormValidation />
          <hr />
          <SimpleValidation />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VuelidateFormValidation from "./components/VuelidateFormValidation";
import SimpleValidation from "./components/SimpleValidation";
export default {
  name: "App",
  components: {
    VuelidateFormValidation,
    SimpleValidation,
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
