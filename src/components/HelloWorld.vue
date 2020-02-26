<template lang="pug">
  .container
    h1(v-text="msg")
    button(v-on:click="onClick") Click me
    div {{fullName}}

</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      user: {
        firtName: 'Pepe',
        lastName: 'Lotudo'
      }
    }
  },
  methods: {
    onClick(){

    }
  },
  computed: {
    fullName() {
      return `${this.user.firtName} ${this.user.lastName}`;
    }
  },
  props: {
    message: {
      type: String,
      default: 'Mensajee by default'
    }
  }
}
</script>


<style scoped>
  .container {
    background-color: darkgreen;
  }
</style>
