<template>
  <div class="dropdown">
    <button class="dropButton" @click="displayTeams">{{ selectedTeam }}</button>
    <div v-for="team in teams" v-show="isTeamDisplayed" :key="team.name">
      <button class="selectedTeams" @click="selectTeam(team)">{{team.name}}</button>
    </div>
  </div>
</template>

<script>

var nbaTeams = [
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
  name: "Team",
  data: function () {
    return {
      teams: nbaTeams,
      selectedTeam: "Select a team",
      isTeamDisplayed: false,
    }
  },
  methods: {
    displayTeams: function (){
      this.isTeamDisplayed = ! this.isTeamDisplayed;
    },
    selectTeam: function (clickedTeam){
      this.selectedTeam = clickedTeam.name;
      this.isTeamDisplayed = false;
    },
  }
}
</script>

<style scoped>
    button {
      width: 18em;
    }

    .dropButton{
      margin-bottom: 1em;
    }
</style>