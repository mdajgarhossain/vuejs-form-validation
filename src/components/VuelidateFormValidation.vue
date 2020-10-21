<template>
  <form id="calculation-form" @submit.prevent="submit">
    <h3 class="text-center font-weight-light">Vuelidate form validation</h3>
    <div class="form-group row">
      <label class="col-sm-3 col-form-label col-form-label-lg"
        >Full Name <span class="text-danger">*</span></label
      >
      <div class="col-sm-9">
        <input
          type="text"
          v-model.trim="$v.fullname.$model"
          :class="{ 'is-invalid': validationStatus($v.fullname) }"
          class="form-control form-control-lg"
        />
        <!-- dispaly the validation error -->
        <div v-if="!$v.fullname.required" class="invalid-feedback">
          This field is required.
        </div>
      </div>
    </div>
    <div class="form-group row">
      <label class="col-sm-3 col-form-label col-form-label-lg"
        >Email <span class="text-danger">*</span></label
      >
      <div class="col-sm-9">
        <input
          type="email"
          v-model.trim="email"
          :class="{ 'is-invalid': validationStatus($v.email) }"
          class="form-control form-control-lg"
        />
        <div v-if="!$v.email.required" class="invalid-feedback">
          This field is required.
        </div>
        <div v-if="!$v.email.email" class="invalid-feedback">
          This email is not valid.
        </div>
      </div>
    </div>
    <!-- <div class="form-group row">
      <label class="col-sm-3 col-form-label col-form-label-lg"
        >Country <span class="text-danger">*</span></label
      >
      <div class="col-sm-9">
        <select
          v-model.trim="country"
          :class="{ 'is-invalid': validationStatus($v.country) }"
          class="form-control form-control-lg"
        >
          <option value="">Select Country</option>
        </select>
      </div>
    </div> -->
    <div class="form-group row">
      <label class="col-sm-3 col-form-label col-form-label-lg"
        >Password <span class="text-danger">*</span></label
      >
      <div class="col-sm-9">
        <input
          type="password"
          v-model.trim="password"
          :class="{ 'is-invalid': validationStatus($v.password) }"
          class="form-control form-control-lg"
        />
        <div v-if="!$v.password.required" class="invalid-feedback">
          This field is required.
        </div>
        <div v-if="!$v.password.minLength" class="invalid-feedback">
          You must have at least {{ $v.password.$params.minLength.min }}.
        </div>
        <div v-if="!$v.password.maxLength" class="invalid-feedback">
          You must have at least {{ $v.password.$params.maxLength.max }}.
        </div>
      </div>
    </div>
    <div class="form-group row">
      <div class="col-sm-12 text-center">
        <button class="btn btn-vue btn-lg col-2">Submit</button>
      </div>
    </div>
  </form>
</template>

<script>
import {
  required,
  email,
  minLength,
  maxLength,
} from "vuelidate/lib/validators";
export default {
  name: "VuelidateFormValidation",
  data() {
    return {
      fullname: "",
      email: "",
      // country: "",
      password: "",
    };
  },
  //validations option in vuelidate for each key
  validations: {
    fullname: { required },
    email: { required, email },
    // country: { required },
    password: { required, minLength: minLength(6), maxLength: maxLength(18) },
  },
  methods: {
    resetData() {
      this.fullname = "";
      this.email = "";
      // country = "",
      this.password = "";
    },
    validationStatus(validation) {
      // console.log(validation);
      return typeof validation != "undefined" ? validation.$error : false;
    },
    submit() {
      //the $touch() method will set true for related models and its children
      this.$v.$touch();
      //prevent submission in case of any error
      if (this.$v.$pendding || this.$v.$error) return;
      console.log("Data submitted!");
      this.$v.$reset();
      this.resetData();
    },
  },
};
</script>

<style>
.btn-vue {
  background: #53b985 !important;
  color: #31485d !important;
  font-weight: bold !important;
}
</style>