<template>
  <div class="display">
    <h1>{{ title }}</h1>
    <div class="forecast-tiles-container">
      <Tile/>
    </div>
  </div>
</template>

<script>
import Tile from './Tile.vue';

export default {
  name: 'title',
  data() {
    return {
      title: 'Forecast',
      buienradarData: {},
    };
  },
  created: function() {
    this.fetchData();
  },
  methods: {
    fetchData: function() {
      this.$http.get('https://xml.buienradar.nl')
        .then(response => {
          this.$set(this, 'buienradarData', response);
        })
    }
  },
  components: {
    Tile,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
  text-align: center;
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
  color: blue;
}

.forecast-tiles-container {
  width: 100%;
  max-width: 1500px;
  height: auto;
  margin: 0 auto;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
