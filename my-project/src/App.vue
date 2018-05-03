<template>
  <div id="app">
    <section class="hero">
        <div class="hero-body">
          <div class="container">
            <h1 class="title">
              {{ landing.title }}
            </h1>
            <h2 class="subtitle">
              {{ landing.subtitle }}
            </h2>
          </div>
        </div>
      </section>

      <section class="section">
        <div class="container">
          <h1 class="title">Section1</h1>
          <h2 class="subtitle section-1">
            {{landing.section1}}
          </h2>
        </div>
      </section>

      <section class="section">
        <div class="container">
          <h1 class="title">Section2</h1>
          <h2 class="subtitle section-2">
            {{landing.section2}}
          </h2>
        </div>
      </section>

      <section class="section">
        <div class="container">
          <h1 class="title">Section3</h1>
          <h2 class="subtitle section-3">
            {{landing.section3}}
          </h2>
        </div>
      </section>

  </div>
</template>

<script>
import { Landing } from './example.tipe';

export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      landing: Landing
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

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
