<template>
  <tr>
    <td class="rank">{{this.rank}}</td>
    <td>
        <div class="dropdown">
          <button class="dropButton" @click="displayTeams" :style="getDuplicateStyle(selectedTeam)"> {{selectedTeam}} </button>
          <div class="selectedTeams" v-for="team in teams" v-show="isTeamDisplayed" :key="team.name">
            <button @click="selectTeam(team)" :style="getDuplicateStyle(team.name)">{{team.name}}</button>
          </div>
        </div>
    </td>
  </tr>
</template>

<script>

export default {
  name: "Team",
  props: ['teams', 'rank', 'duplicate'],
  data: function () {
    return {
      isTeamDisplayed: false,
      selectedTeam: "Select a team",
    }
  },
  methods: {
    displayTeams: function (){
      this.isTeamDisplayed = ! this.isTeamDisplayed;
    },
    selectTeam: function (clickedTeam){
      this.$emit('selectTeam', this.rank, this.selectedTeam.name, clickedTeam.name);
      this.selectedTeam = clickedTeam.name;
      this.isTeamDisplayed = false;
    },
    getDuplicateStyle: function (name) {
      if (this.duplicate.indexOf(name)===-1){
        return {'color': 'black'}
      } else {
        return {'color': 'red'}
      }
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

    tr {
      border: 1px solid black;
    }

    td {
      border-left: 1px solid black;
      border-right: 1px solid black;
    }
</style>