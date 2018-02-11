<template>
  <div class="forecast-tile">
    <div class="tile-above">
      <span class="temperature">{{oneDay.maxtemp}}<span class="celcius">°</span>  </span>
      <span class="day-name">{{fullDayName(oneDay.dagweek)}}</span>
      <span class="date">{{removeDayFromDate(oneDay.datum)}}</span>
    </div>
    <div class="tile-underneath">

      <div class="weather-information">
        <div class="item">
          <span>Minimumtemperatuur</span>
          <span>{{oneDay.mintemp}}°</span>
        </div>
        <div class="item">
          <span>Maximumtemperatuur</span>
          <span>{{oneDay.maxtemp}}°</span>
        </div>
        <div class="item">
          <span>Neerslagkans</span>
          <span>{{oneDay.kansregen}}%</span>
        </div>
        <div class="item">
          <span>Zonneschijn</span>
          <span>{{oneDay.kanszon}}%</span>
        </div>
        <div class="item">
          <span>Windkracht</span>
          <span>{{oneDay.windkracht}} bft</span>
        </div>
        <div class="item">
          <span>Windrichting</span>
          <span>{{oneDay.windrichting}}</span>
        </div>
      </div>

    </div>
  </div>
</template>

<script>

export default {
  name: 'Tile',
  props: ['oneDay'],
  data() {
    return {

    };
  },
  created: function () {
  },
  methods: {
    fullDayName: function (dayName) {
      switch (dayName) {
        case 'ma':
          return 'Maandag';
          break;
        case 'di':
          return 'Dinsdag';
          break;
        case 'wo':
          return 'Woensdag';
          break;
        case 'do':
          return 'Donderdag';
          break;
        case 'vr':
          return 'Vrijdag';
          break;
        case 'za':
          return 'Zaterdag';
          break;
        case 'zo':
          return 'Zondag';
          break;
        default:
          return 'Dag'
      }
    },
    removeDayFromDate: function (str) {
      return str.substring(str.indexOf(" ") + 1);
    }
  }
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
  box-shadow: 0 0 40px #e2e2e2;
  border-radius: 20px;
  height: 475px;
  width: 300px;
  margin: 32px 32px;
  position: relative;
  overflow: hidden;
}

.tile-above {
  height: 50%;
  width: 100%;
  display: flex;
  justify-content: center;
  flex-direction: column;
  background: #fff;
}

/*
  Purple color: #5F4BB6
  Dark font color: #202A25
  Light font color: #CECECE

*/

.tile-above .temperature {
  font-size: 60px;
  color: #5F4BB6;
  position: relative;
}

.tile-above .temperature .celcius {
  font-size: 40px;
  color: #CECECE;
  position: absolute;
  top: 8px;
}

.tile-above .day-name {
  font-size: 32px;
}

.tile-underneath {
  width: 100%;
  height: 50%;
  background: #fcfcfc;
  position: relative;
  border-top: 3px solid #5F4BB6;
}

.tile-underneath .weather-information {
  width: 100%;
  display: flex;
  justify-content: flex-start;
  flex-direction: column;
  flex-wrap: wrap;
  align-content: flex-start;
  margin-top: 8px;
}

.tile-underneath .weather-information .item {
  font-size: 14px;
  width: auto;
  text-align: left;
  padding: 8px 16px;
  display: flex;
  justify-content: space-between;
  position: relative;
}

.tile-underneath .weather-information .item:before {
  content: '';
  position: absolute;
  display: block;
  width: calc(100% - 32px);
  height: 1px;
  background: #EFEFEF;
  bottom: 3px;
}


</style>
