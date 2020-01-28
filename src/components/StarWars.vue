<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      This website is using The Star Wars API
      <a
        href="https://swapi.co/"
        target="_blank"
        rel="noopener"
      >Swapi API</a>.
    </p>
    <button v-on:click="getStarWarsData">Get planet names</button>
    <ul>
      <li v-for="item in starWarsData.results" :key="item.diameter">{{ item.name }}</li>
    </ul>
    <div>{{ starWarsData }}</div>
  </div>
</template>

<script>
export default {
  name: "StarWars",
  props: {
    msg: String
  },
  data: function() {
    return {
      starWarsData: []
    };
  },
  methods: {
    getStarWarsData() {
      fetch("https://swapi.co/api/planets/")
        .then(response => response.json())
        .then(data => (this.starWarsData = data));
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
