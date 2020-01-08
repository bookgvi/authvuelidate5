<template>
  <b-container>
    <b-form @submit.prevent="onSubmit">
      <b-row align-h="center">
        <b-col cols="4" align="start">
          <label class="w-100">
            Input #1:
            <b-form-input v-model="input1"/>
          </label>
        </b-col>
      </b-row>
      <b-row align-h="center">
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
      input1: ''
    }
  },
  methods: {
    onSubmit () {}
  }
}
</script>

<style scoped>

</style>
