<template>
  <div id="app">
    <Note :notes='notes' text="hello everyone a note!"/>
  </div>
</template>

<script>
import Note from './components/Note.vue'

export default {
  name: 'App',
  components: {
    Note
  },
  data() {
    return {
      notes: [
        {
          text: 'a note',
          quote: 'a thousand years',
          url: 'https://google.com'
        },
        {
          text: 'a second note',
          quote: 'a thousand years',
          url: 'https://google.com'
        }
      ]
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
