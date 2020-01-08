<template>
  <b-container>
    <b-form @submit.prevent="onSubmit">
      <b-input-component
        :inputVal="input1"
        @hInput="hInput"
      />
      <div v-if="!input1.validate" class="error"> * Поле обязательно для заполнения </div>
      <b-input-component
        :inputVal="input2"
        @hInput="hInput"
      />
      <div v-if="!input2.validate" class="error"> * Поле обязательно для заполнения </div>
      <b-row align-h="center" class="mt-3">
        <b-col cols="4" align="start">
          <b-button type="submit" class="w-100"> Click me </b-button>
        </b-col>
      </b-row>
    </b-form>
  </b-container>
</template>

<script>
import BInputComponent from '@/components/VuelidateForm/inputComponent'
export default {
  name: 'vuelidateForm',
  components: { BInputComponent },
  data () {
    return {
      self: this,
      input1: {
        inputValue: '',
        validate: true,
        inputKey: 'input1'
      },
      input2: {
        inputValue: '',
        validate: true,
        inputKey: 'input2'
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
    hInput ({ e, val, validate }) {
      this[val].inputValue = e.target.value
      this[val].validate = validate
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
