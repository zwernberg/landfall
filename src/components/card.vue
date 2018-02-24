<template>
  <b-card border-variant="dark"
            :header=data.name
            header-bg-variant="dark"
            footer-bg-variant="dark"
            :footer="`Cost $${data.usd}`"
            header-text-variant="white"
            footer-text-variant="white">
      <p class="card-text"><cardText  :text=data.oracle_text></cardText></p>
    </b-card>
</template>

<script>
import cardText from '@/components/cardText';
export default {
  name: 'card',
  components: {
    cardText,
  },
  props: ['data'],
  data () {
    return {
      msg: ''
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
