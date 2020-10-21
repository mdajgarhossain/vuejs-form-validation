<template>
  <form id="simple-form" @submit.prevent="checkForm">
    <h3 class="text-center font-weight-light">
      Vuejs cookbook form validation
    </h3>
    <div v-if="errors.length">
      <b>Please correct the following error(s):</b>
      <ul>
        <li v-for="(error, index) in errors" :key="index" class="text-danger">
          {{ error }}
        </li>
      </ul>
    </div>
    <div class="form-group row">
      <label for="name" class="col-sm-3 col-form-label col-form-label-lg"
        >Name <span class="text-danger">*</span></label
      >
      <div class="col-sm-9">
        <input
          v-model="name"
          id="name"
          type="text"
          name="name"
          class="form-control form-control-lg"
        />
      </div>
    </div>
    <div class="form-group row">
      <label for="age" class="col-sm-3 col-form-label col-form-label-lg"
        >Age <span class="text-danger">*</span></label
      >
      <div class="col-sm-9">
        <input
          v-model="age"
          id="age"
          type="number"
          name="age"
          class="form-control form-control-lg"
        />
      </div>
    </div>
    <div class="form-group row">
      <label for="movie" class="col-sm-3 col-form-label col-form-label-lg"
        >Favorite Movie</label
      >
      <div class="col-sm-9">
        <select
          v-model="movie"
          id="movie"
          name="movie"
          class="form-control form-control-lg"
        >
          <option>Omar Series</option>
          <option>Bayuk Selcuk</option>
          <option>The Ottoman Empire</option>
        </select>
      </div>
    </div>
    <div class="form-group row">
      <div class="col-sm-12 text-center">
        <button type="submit" value="Submit" class="btn btn-vue btn-lg col-2">
          Submit
        </button>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  name: "SimpleValidation",
  data() {
    return {
      errors: [],
      name: null,
      age: null,
      movie: null,
    };
  },
  methods: {
    checkForm() {
      if (this.name && this.age) {
        console.log(this.name, this.age);
        this.errors = [];
        return true;
      }

      this.errors = [];

      if (!this.name) {
        this.errors.push("Name is required");
      }
      if (!this.age) {
        this.errors.push("Age is required");
      }

      // e.preventDefault();
    },
  },
};
</script>

<style>
</style>