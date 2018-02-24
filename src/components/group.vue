<template>
  <b-jumbotron>
    <!-- <h1>{{data}}</h1> -->
    <h1><i v-for="(mana, index) in color_identity" :class="`ms ms-${toLower(mana)} ms-cost group-mana`" :key="index"></i></h1>
    <b-card-group deck class="md-3" v-for="(group, index) in card_groups" :key="index">
      <card v-for="(card, index) in group" :data=card :key="index"> </card>
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
  },
  computed: {
    color_identity: function () {
      if (this.data[0].color_identity.length === 0) {
        return ('c');
      } else {
        return this.data[0].color_identity;
      }
    },
    card_groups: function () {
      return this._.chunk(this.data, 3);
    }
  },
  created() {
    //
  },
  methods: {
    toLower(s) {
      return s.toLowerCase();
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
