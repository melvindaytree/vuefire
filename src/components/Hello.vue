<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <b-alert show variant="info">Primary Alert</b-alert>

    <sidebar></sidebar>

    <b-container class="bv-example-row">
      <agenttable></agenttable>
      <hr>
      <br>
      <testtable></testtable>
      <hr>

      <div>
        <b-card  bg-variant="light" text-variant="black" title="Other Stuff">
        <p class="card-text">
          With supporting text below as a natural lead-in to additional content.
        </p>
        <b-button href="#" variant="primary">Go somewhere</b-button>
        </b-card>
      </div>

    </b-container>
        


</div>
</template>

<script>
import sidebar from './sidebar'
import testtable from './testtable'
import agenttable from './agenttable'


export default {
  name: 'hello',
  components: {
    'sidebar': sidebar,
    'testtable': testtable,
    'agenttable': agenttable,
  },

  
  data () {
    return {
      msg: 'Welcome to Your Home',
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
