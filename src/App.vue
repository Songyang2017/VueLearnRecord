<template>
  <img
    alt="Vue logo"
    src="./assets/logo.png"
  >
  <HelloWorld
    msg="Welcome to Your Vue.js App"
    :count="count"
  />
  <button @click="change">变更</button>
</template>

<script>
import { reactive, toRefs } from '@vue/reactivity'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  setup () {
    const data = reactive({
      count: 0
    })

    const change = () => {
      data.count++
    }
    const _data = toRefs(data)
    return {
      ..._data,
      change
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
