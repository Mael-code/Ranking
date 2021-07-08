<template>
  <div class="dropdown">
    <button class="dropButton" @click="displayTeams">{{ selectedTeam }}</button>
    <div class="selectedTeams" v-for="team in teams" v-show="isTeamDisplayed" :key="team.name">
      <div><button   @click="selectTeam(team)">{{team.name}}</button></div>
    </div>
  </div>
</template>

<script>

export default {
  name: "Team",
  props: ['teams'],
  data: function () {
    return {
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
    .dropButton {
      margin: 1em;
    }

    button {
      width: 18em;
      margin: 1px;
    }
</style>