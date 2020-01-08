<template>
  <b-container>
    <b-form @submit.prevent="onSubmit">
      <b-row align-h="center">
        <b-col cols="4" align="left">
          <label class="w-100">
            Input #1:
            <b-form-input :value="input1.inputValue" @input.native="hInput($event, 'input1')" :class="{ error: !input1.validate }" />
            <div v-if="!input1.validate" class="error"> * Поле обязательно для заполнения </div>
          </label>
        </b-col>
      </b-row>
      <b-row align-h="center">
        <b-col cols="4" align="left">
          <label class="w-100">
            Input #2:
            <b-form-input :value="input2.inputValue" @input.native="hInput($event, 'input2')" :class="{ error: !input2.validate }" />
            <div v-if="!input2.validate" class="error"> * Поле обязательно для заполнения </div>
          </label>
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
      self: this,
      input1: {
        inputValue: '',
        validate: true
      },
      input2: {
        inputValue: '',
        validate: true
      }
    }
  },
  methods: {
    onSubmit () {
      let isInput = true
      let i = 1
      do {
        if (this[`input${i}`]) {
          this[`input${i}`].validate = String(this[`input${i}`].inputValue).length > 0
          i++
        } else {
          isInput = false
        }
      } while (isInput)
    },
    hInput (e, val) {
      this[val].validate = true
      this[val].inputValue = e.target.value
    }
  }
}
</script>

<style>
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
