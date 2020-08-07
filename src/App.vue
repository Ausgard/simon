<template>
  <div id="app">
  <simonSay
  :gameBoard="gameBoard"
  />
  </div>
</template>

<script>
import simonSay from '@/components/simonSay'
export default {
  name: 'App',
  components: {
    simonSay
  },
  data() {
    return {
      gameBoard: [
        {id: 1, title: 'blue', completed: false},
        {id: 2, title: 'red', completed: false},
        {id: 3, title: 'yellow', completed: false},
        {id: 4, title: 'green', completed: false}
      ],
    }
  }
} 
</script>

<style lang="sass">
#app
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center
  color: #2c3e50
</style>
