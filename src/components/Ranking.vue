<template>
  <table>
    <thead>
    <tr>
      <th class="rank">Rank</th>
      <th>Team</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="i in teams.length" :key="i">
      <td class="rank">{{i}}</td>
      <td><div class="teamButton"><Team  :teams="teams"></Team></div></td>
    </tr>
    </tbody>
  </table>
</template>

<script>

import Team from './Team.vue'

export default {
  name: "Ranking",
  components: {
    Team
  },
  props: ['teams']

}
</script>

<style scoped>

table {
  border: 1px solid black;
  border-collapse: collapse;
}

td, th {
  border-left: 1px solid black;
  border-right: 1px solid black;
}

tr {
  border: 1px solid black;
}

teamButton {
  vertical-align: bottom;
}

.rank {
  width: 4em;
}

</style>