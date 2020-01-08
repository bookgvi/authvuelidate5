<template>
  <b-row align-h="center">
    <b-col cols="4" align="left">
      <label class="w-100">
        Input:
        <b-form-input :value="inputVal.inputValue" @input.native="hInput($event, inputVal.inputKey)" :class="{ error: !inputVal.validate }" />
      </label>
    </b-col>
  </b-row>
</template>

<script>
export default {
  name: 'bInputComponent',
  props: {
    inputVal: {
      type: Object
    }
  },
  methods: {
    hInput (e, val) {
      const validate = String(e.target.value).length > 0
      this.$emit('hInput', { e, val, validate })
    }
  }
}
</script>

<style scoped>

</style>
