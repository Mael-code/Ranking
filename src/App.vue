<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/nba_logo.png">

    <table id="selector">
      <tr>
        <td><button @click="displayRanking('allTeamRanking')">NBA ranking</button></td>
        <td><button @click="displayRanking()">Conference Ranking</button></td>
        <td><button @click="displayRanking('division')">Division Ranking</button></td>
      </tr>
    </table>
    <Ranking v-show="displayNbaRank" :teams=nbaTeams></Ranking>

    <table v-show="displayConference">
      <tr>
        <td><Ranking :teams="westernConference"></Ranking></td>
        <td id="space"></td>
        <td><Ranking :teams="westernConference"></Ranking></td>
      </tr>
    </table>
  </div>
</template>

<script>
import Ranking from './components/Ranking.vue'

const southwestDivision = [
  { name:"Mavericks de Dallas"},
  { name: "Rockets de Houston"},
  { name: "Grizzlies de Memphis"},
  { name: "Pelicans de La Nouvelle-Orléans"},
  { name: "Spurs de San Antonio"},
];

const pacificDivision = [
  { name: "Suns de Phoenix"},
  { name: "Clippers de Los Angeles"},
  { name: "Lakers de Los Angeles"},
  { name: "Kings de Sacramento"},
  { name:"Warriors de GoldenState"},
];

const northwestDivision = [
  { name:"Nuggets de Denver"},
  { name: "Jazz de l'Utah"},
  { name: "Thunder d'Oklahoma City"},
  { name: "Trail Blazers de Portland"},
  { name: "Timberwolves du Minnesota"},
];

const atlanticDivision = [
  { name: "76ers de Philadelphie"},
  { name: "Nets de Brooklyn"},
  { name: "Knicks de New York"},
  { name:"Celtics de Boston"},
  { name: "Raptors de Toronto"},
];

const centralDivision = [
  { name: "Bucks de Milwaukee"},
  { name: "Bulls de Chicago"},
  { name: "Cavaliers de Cleveland"},
  { name: "Pacers de l'Indiana"},
  { name: "Pistons de Détroit"},
];

const southeastDivision = [
  { name: "Heat de Miami"},
  { name: "Hawks d'Atlanta"},
  { name: "Wizards de Washington"},
  { name: "Hornets de Charlotte"},
  { name: "Magic d'Orlando"},
];

const easternConference =  centralDivision.concat(southeastDivision).concat(atlanticDivision);
const westernConference = southwestDivision.concat(northwestDivision).concat(pacificDivision);

export default {
  name: 'App',
  components: {
    Ranking,
  },
  data: function (){
    return {
      nbaTeams: easternConference.concat(westernConference),
      easternConference: easternConference,
      westernConference: westernConference,
      displayDivision: false,
      displayConference: true,
      displayNbaRank: false,
    }
  },
  methods:{
    displayRanking: function (rankingToDisplay) {
      this.displayDivision=false;
      this.displayConference=false;
      this.displayNbaRank=false;

      if (rankingToDisplay==="division"){
        this.displayDivision = true;
      }
      else if(rankingToDisplay==="allTeamRanking"){
        this.displayNbaRank = true;
      }
      else{
        this.displayConference =true;
      }
    }
  },
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

#selector td {
  padding: 3em;
}

#selector button {
  height: 4em;
  width: 16em;
}

#space {
  padding: 2em;
}

table {
  margin: 2em auto 2em auto;
}

img {
  height: 10em;
  width: auto;
}

</style>
