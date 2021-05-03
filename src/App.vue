<template>
  <div id="app">
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  data() {
    return {
    }
  },
  async mounted() {
    await liff.init({
      liffId: '1655949010-8b2R7KdL'
    })

    if (liff.isInClient()) {
      try {
        const idToken = liff.getIDToken()
        await axios({
          method: 'POST',
          url: 'https://7e4ff68b646f.ngrok.io/auth/connect/line',
          data: {
            idToken
          }
        })
      } catch (err) {
        console.error(err.message)
      }
    }
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
