<template>
  <div class="display">
    <h1>{{ title }}</h1>
    <div class="forecast-tiles-container">
      <Tile v-for="oneDay in fiveDays" :oneDay="oneDay" />
    </div>
  </div>
</template>

<script>
import Tile from './Tile.vue';
import { parseString } from 'xml2js';

export default {
  name: 'display',
  data() {
    return {
      title: '5-daagse verwachting',
      fiveDays: [],
      allData: [],
    };
  },
  created: function () {
    this.fetchData();
  },
  methods: {
    fetchData: function () {
      this.$http.get('https://xml.buienradar.nl')
        .then(({ data: xml }) => {
          parseString(xml,
            { trim: true, explicitArray: false, preserveChilden: true },
            (error, parsed) => {

              const allData = parsed.buienradarnl;
              this.allData.push(allData);

              const moreDaysData = parsed.buienradarnl.weergegevens.verwachting_meerdaags;
              const moreDays = [];

              for (let i = 0; i < 5; i += 1) {
                const oneDayData = moreDaysData[`dag-plus${i + 1}`];
                this.fiveDays.push(oneDayData);
              }
            });
        });
    },
  },
  components: {
    Tile,
  }
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
  max-width: 100%;
  height: auto;
  margin: 0 auto;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
