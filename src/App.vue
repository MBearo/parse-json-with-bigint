<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Parse from './assets/parse.js'

export default {
  name: 'app',
  components: {
    HelloWorld
  },
  mounted () {
    console.log(Parse()('{"a":123456123456123456}'))

    const xhr = new XMLHttpRequest()
    xhr.withCredentials = true
    xhr.open('get', '接口地址')
    xhr.send(null)
    xhr.onreadystatechange = () => {
      if (xhr.readyState === 4) {
        console.log(xhr.responseText)
        // 比如
        // console.log((Parse()(xhr.responseText).data.rows[0].order_id.toString()))
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
