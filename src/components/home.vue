<template>
  <div class="home">
    <b-jumbotron><h1>Mana Combinations</h1></b-jumbotron>
    <div v-for="(group, index) in groups" :key="index">
      <group :data=group></group>
    </div>
  </div>
</template>

<script>
import group from '@/components/group.vue';
import json from '@/data/cards.json';
export default {
  name: 'home',
  components: {
    group,
  },
  data () {
    return {
      groups: json.groups
    }
  }
}
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
  color: #42b983;
}
</style>
