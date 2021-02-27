<template>
  <div id="app">
    <button @click="backendTest"> Daten aus DB laden</button>
    {{ test }}
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      test: 'test'
    }
  },
  methods: {
    async backendTest() {
        this.test = await this.axios
          .get('https://bkrugtestapi.azurewebsites.net/test', {
            headers: {"Access-Control-Allow-Origin": "*"}
          })
          .then(response => {
            return response.data
          })
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
