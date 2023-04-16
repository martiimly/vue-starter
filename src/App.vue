<template>
  <div class="my-app">
    <div v-if="loggedIn">
      <h1>Witaj w systemie do zapisów na zajęcia</h1>
      <p>Witaj {{ authenticatedUsername }} !</p>
      <button @click="logMeOut">Wyloguj</button></div>

    <div v-else>
<!--      <h1>Witaj w systemie do zapisów na zajęcia</h1>-->
<!--      <div>Zaloguj się e-mailem <input type="email" v-model="email">-->
<!--        <button @click="logMeIn">Wchodzę</button></div>-->
      <LoginForm @login="(username) => logMeIn(username)" button-label="Wejdź"></LoginForm>
      <LoginForm @login="(username) => logMeIn(username)" button-label="Wleć"></LoginForm>
      <LoginForm @login="(username) => logMeIn(username)" :button-label="Math.random() < 0.5 ? 'Etykieta A' : 'Etykieta B'"></LoginForm>

<!--      <LoginForm @login="(username) => logMeIn(username)"></LoginForm>-->
    </div>
  </div>
<!--    <div v-if="email.length < 10">({{email.length}}) Ale masz krótki adres!</div>-->
<!--    <div v-else-if="email.length < 15">({{email.length}}) Twój adres e-mail jest w sam raz.</div>-->
<!--    <div v-else>({{email.length}}) Twój adres e-mail jest stanowczo za długi.</div>-->
<!--    <div v-if="!email.includes('@')">Twój email nie zawiera @!!</div>-->
</template>

<script>
import LoginForm from "./LoginForm";
import "milligram";
export default {
  components: {LoginForm},
  methods: {
    logMeIn(username) {
      this.authenticatedUsername = username;
      this.loggedIn = true;},
    logMeOut() {
      this.loggedIn = false;
    this.authenticatedUsername = ''}

  },
  data() {
    return {
      authenticatedUsername: '',
      password: '',
      loggedIn: false,
    };
  }
}
</script>

<style>
.my-app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
}
</style>
