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
import axios from 'axios';

export default {
  name: 'home',
  components: {
    group,
  },
  data () {
    return {
      groups: []
    }
  },
  created () {
    // fetch the data when the view is created and the data is
    // already being observed
    this.fetchData()
  },
  methods :{
    fetchData() {
      axios.get('https://api.scryfall.com/cards/search?order=cmc&q=t:land+f%3Astandard+not:transform')
      .then(response => {
        const cards = response.data.data;
        // test
        this.groups = this._.groupBy(cards, function(test) {
          return test.color_identity.join('');
        });
        this.groups = this._.orderBy(this.groups, cards => { return cards[0].color_identity.length });
      })
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
