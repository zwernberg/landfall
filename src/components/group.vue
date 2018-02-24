<template>
  <b-jumbotron>
    <h1>{{data.name}}</h1>
    <h1><i v-for="(mana, index) in data.symbols" :class="`ms ms-${mana} ms-cost group-mana`" :key="index"></i></h1>
    <b-card-group deck class="columns">
    <card v-for="(card, index) in data.cards" :data=card :key="index"> </card>
    </b-card-group>
  </b-jumbotron>
</template>

<script>
import card from '@/components/card';
export default {
  name: 'group',
  props: ['data'],
  components: {
    card,
  },
  data () {
    return {
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

.group-mana {
  margin-left: 15px;
  margin-right: 15px;
}
</style>
