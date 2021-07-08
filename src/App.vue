<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Ranking :teams=nbaTeams></Ranking>
  </div>
</template>

<script>
import Ranking from './components/Ranking.vue'

var nbaAllTeams = [
  { name:"Nuggets de Denver"},
  { name:"Warriors de GoldenState"},
  { name:"Mavericks de Dallas"},
  { name:"Celtics de Boston"},
  { name: "Bulls de Chicago"},
  { name: "Hawks d'Atlanta"},
  { name: "Timberwolves du Minnesota"},
  { name: "Clippers de Los Angeles"},
  { name: "Rockets de Houston"},
  { name: "Nets de Brooklyn"},
  { name: "Cavaliers de Cleveland"},
  { name: "Hornets de Charlotte"},
  { name: "Thunder d'Oklahoma City"},
  { name: "Lakers de Los Angeles"},
  { name: "Grizzlies de Memphis"},
  { name: "Knicks de New York"},
  { name: "Pistons de Détroit"},
  { name: "Heat de Miami"},
  { name: "Trail Blazers de Portland"},
  { name: "Suns de Phoenix"},
  { name: "Pelicans de La Nouvelle-Orléans"},
  { name: "76ers de Philadelphie"},
  { name: "Pacers de l'Indiana"},
  { name: "Magic d'Orlando"},
  { name: "Jazz de l'Utah"},
  { name: "Kings de Sacramento"},
  { name: "Spurs de San Antonio"},
  { name: "Raptors de Toronto"},
  { name: "Bucks de Milwaukee"},
  { name: "Wizards de Washington"},
];

export default {
  name: 'App',
  components: {
    Ranking,
  },
  data: function (){
    return {
      nbaTeams: nbaAllTeams
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
