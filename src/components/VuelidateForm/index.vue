<template>
  <b-container>
    <b-form @submit.prevent="onSubmit">
      <b-row align-h="center">
        <b-col cols="4" align="start">
          <label class="w-100">
            Input #1:
            <b-form-input :value="input1" @input.native="hInput($event, 'input1', 'valid')" :class="{ error: !valid }"/>
          </label>
          <div v-if="!valid" class="error"> * Поле обязательно для заполнения </div>
        </b-col>
      </b-row>
      <b-row align-h="center" class="mt-3">
        <b-col cols="4" align="start">
          <b-button type="submit" class="w-100"> Click me </b-button>
        </b-col>
      </b-row>
    </b-form>
  </b-container>
</template>

<script>
export default {
  name: 'vuelidateForm',
  data () {
    return {
      input1: '',
      valid: true
    }
  },
  methods: {
    onSubmit () {
      this.valid = String(this.input1).length > 0
    },
    hInput (e, inputVal, validator) {
      this[validator] = true
      this[inputVal] = e.target.value
    }
  }
}
</script>

<style scoped>
  .error {
    color: red;
    font-size: 0.7em;
  }
  input.error {
    font-size: 1rem;
    border-color: red;
  }
  input.error:active, input.error:focus {
    border: 2px solid red;
    outline-color: red;
    box-shadow: none !important;
  }
</style>
