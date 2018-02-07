<template>
  <div class="forecast-tile">
  </div>
</template>

<script>

export default {
  name: 'Tile',
  data() {
    return {
      title: 'Five day weather forecast of The Netherlands',
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
  color: blue;
}

.forecast-tile {
  box-shadow: 0 0 40px #e2e2e2e2;
  border-radius: 20px;
  height: 400px;
  width: 300px;
}
</style>
