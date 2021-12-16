<template>
  <div class="about">
    <h1>
      current team: {{searchName(teamId)}}
    </h1>
    <p>
      <button @click="countUp(searchName(teamId))">counter</button>
    </p>
    <p>
      {{$store.state.sum}}
    </p>
    <p>
      Last team name clicked: {{$store.state.lastTeam}}
    </p>
    <p class="back" @click="back">
      戻る
    </p>
  </div>
</template>


<script>
export default {
  data() {
    return {
      teams: [
        {
          id: "c36136ef-552f-4dc9-84b6-65ecb8574e81",
          name: "Team_A",
        },
        {
          id: "ed0459f5-716d-4ef4-99ba-5dc750dfe0d0",
          name: "Team_B",
        },
        {
          id: "60d0d5d5-8ce9-41d9-a65b-13a090c10ae1",
          name: "Team_C",
        },
      ]
    };
  },
  props:[
    "teamId"
  ],
  methods:{
    searchName(id){
      let name = "";
      this.teams.forEach(value =>{
        if(value.id === id){
          name = value.name;
        }
      });
      return name;
    },
    countUp(name){
      this.$store.commit("countUp",name);
    },
    back(){
      this.$router.push({name:"Home"});
    }
  }
};
</script>

<style scoped>
.back{
  cursor: pointer;
}
</style>