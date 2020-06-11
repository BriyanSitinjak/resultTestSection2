<template>
  <div>
      <h2> Total Data Covid-19!</h2>
    <ul>
      <li v-for="u in users" :key="u.id">
        <p> Last Update on : {{ u.last_update }} </p> 
        <p> Confirmed : {{ u.confirmed }} </p> 
        <p> Recovered : {{ u.recovered }} </p> 
        <p> Active : {{ u.active }} </p> 
      </li>
      <button @click="load"> Load Data </button> <br/>
    </ul>
    <ol>
      <h2> Check Region</h2>
      <li v-for="u in users" :key="u.id">
        <p>{{ u.name }} </p> 
      </li>
      <button @click="region"> Data Region </button> <br/>
    </ol>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    
    data() {
      return {
        users : []
      }
    },

    async mounted() {
      // this.load
    },

    methods: {
      async load() {
      const response = await axios.get(`https://covid-api.com/api/reports/total?date=2020-06-09`)

      console.log(response.data)
      this.users = response.data
    },

     async region() {
      const response = await axios.get(`https://covid-api.com/api/regions`)

      console.log(response.data)
      this.country = response.data
    }
    }
  }

</script>