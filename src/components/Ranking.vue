<template>
  <table>
    <thead>
    <tr>
      <th class="rank">Rank</th>
      <th>Team</th>
    </tr>
    </thead>
    <tbody>
      <Team v-for="i in teams.length" @selectTeam=selectTeam :key=i  :teams=teams :rank=i :duplicate=duplicate></Team>
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
  props: ['teams'],
  data: function () {
    return {
      ranking: [],
      duplicate: [],
    }
  },
  methods : {
    selectTeam: function (index,oldName,newName) {
      this.ranking[index-1] = newName;
      this.setDuplicate(oldName,newName);
    },
    setDuplicate: function (oldName,newName) {
      if (oldName === newName) {
        return;
      }

      let oldOc = [];
      let newOc = [];
      let i=0;
      while(i<this.ranking.length){
        if (this.ranking[i]===oldName) {
          oldOc.push(i);
        }
        else if (this.ranking[i]==newName){
          newOc.push(i);
        }
        i++;
      }

      if (oldOc.length===1){
        this.duplicate = this.duplicate.slice(this.duplicate.indexOf(oldName),1);
      }
      if (newOc.length>1 && this.duplicate.indexOf(newName)===-1){
        this.duplicate.push(newName);
      }
    },
  },

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



teamButton {
  vertical-align: bottom;
}

.rank {
  width: 4em;
}

</style>