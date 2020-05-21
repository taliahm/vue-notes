<style>
  :root {
    --back: #cde7c2;
    --text: #25224A;
    --highlight: #69D8C4;
    --blueHighlight: #3E50F5;
    --white: #D9E0F5;
  }
  * {
    box-sizing: border-box;
  }
  body {
    background: var(--back);
    margin-top: 0px;
  }
</style>
<template>
  <div id="app">
    <h1>Saved Musings...</h1>
    <Notes :getNotes='getNotes' :notes='notes' text="hello everyone a note!"/>
  </div>
</template>

<script>
import Notes from './components/Notes.vue'

export default {
  name: 'App',
  components: {
    Notes
  },
  methods: {
  getNotes() {
    fetch('http://localhost:3000/notes').then(res => {
      return res.json();
    }).then(json => {
      console.log(json);
      this.notes = json.data;
    })
  },
  },
  data() {
    return {
      notes: []
    }
  },
  mounted() {
    this.getNotes()
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
