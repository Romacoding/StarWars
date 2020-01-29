<template>
  <div>
    <h1>{{ msg }}</h1>
    <p>
      This website is using The Star Wars API
      <a
        href="https://swapi.co/"
        target="_blank"
        rel="noopener"
      >Swapi API</a>.
    </p>
    <h2>Star Wars planets:</h2>
    <input
      type="text"
      v-model.trim="search"
      placeholder="Search planets..."
      @keyup="getAllStarWarsPlanets"
    />
    <br />
    <ul>
      <li v-for="item in starWarsData" :key="item.orbital_period">{{ item.name }}</li>
    </ul>
    <!--     <div>{{ starWarsData }}</div> -->
  </div>
</template>

<script>
export default {
  name: "StarWars",
  props: {
    msg: String
  },
  data() {
    return {
      starWarsData: [],
      search: ""
    };
  },
  methods: {
    getAllStarWarsPlanets() {
      fetch("https://swapi.co/api/planets/")
        .then(response => response.json())
        .then(res => {
          if (this.search) {
            this.starWarsData = res.results.filter(starWarsData =>
              starWarsData.name
                .toLowerCase()
                .includes(this.search.toLowerCase())
            );
          } else {
            this.starWarsData = res.results;
          }
        });
    }
  },
  created() {
    this.getAllStarWarsPlanets();
  }
};
</script>

<!-- Added "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  display: flex;
  flex-direction: column;
  list-style-type: none;
  padding: 0;
}
li {
  margin: 10px 10px;
}
a {
  color: #ce9e03;
}
</style>
