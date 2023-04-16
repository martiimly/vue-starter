<template>
<div>
<label>Zaloguj się e-mailem</label>
<input type="email" v-model="authenticatedUsername">
<button @click="enter()">Zaloguj się</button>
</div>
</template>

<script>
export default {
  props: {buttonLabel: String},
  data() {
    return {
      authenticatedUsername: ''
    }
  },
  methods: {
    enter() {
      this.$emit('login', this.authenticatedUsername);

    }
  }
}
</script>