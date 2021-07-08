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
      <thead>
      <tr>
        <td>Western Conference</td>
        <td class="space"></td>
        <td>Eastern Conference</td>
      </tr>
      </thead>
      <tbody>
        <tr>
          <td><Ranking :teams="westernConference"></Ranking></td>
          <td class="space"></td>
          <td><Ranking :teams="easternConference"></Ranking></td>
        </tr>
      </tbody>
    </table>

    <table id="division" v-show="displayDivision">
      <thead>
      <td>Southwest Division</td>
      <td class="space"></td>
      <td>Pacific Division</td>
      <td class="space"></td>
      <td>Northwest Division</td>
      <td class="space"></td>
      <td>Atlantic Division</td>
      <td class="space"></td>
      <td>Central Division</td>
      <td class="space"></td>
      <td>Southeast Division</td>
      </thead>
      <tbody>
        <tr>
          <td><Ranking :teams="southwestDivision"></Ranking></td>
          <td class="space"></td>
          <td><Ranking :teams="pacificDivision"></Ranking></td>
          <td class="space"></td>
          <td><Ranking :teams="northwestDivision"></Ranking></td>
          <td class="space"></td>
          <td><Ranking :teams="atlanticDivision"></Ranking></td>
          <td class="space"></td>
          <td><Ranking :teams="centralDivision"></Ranking></td>
          <td class="space"></td>
          <td><Ranking :teams="southeastDivision"></Ranking></td>
        </tr>
      </tbody>
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
      centralDivision: centralDivision,
      southeastDivision: southeastDivision,
      atlanticDivision: atlanticDivision,
      southwestDivision: southwestDivision,
      northwestDivision: northwestDivision,
      pacificDivision: pacificDivision,
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
  padding: 1em;
}

#selector button {
  height: 4em;
  width: 16em;
}

#division .space {
  padding: 0px;
}

.space {
  padding: 2em;
}


table {
  margin: 0 auto 1em auto;
}

img {
  height: 10em;
  width: auto;
}

</style>
