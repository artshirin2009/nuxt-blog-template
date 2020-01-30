<template>
  <div>
    <h1>Город - {{city.title}}</h1>
    <h2>Страна - {{country.title}}</h2>
    <h3>http://{{BACKEND_HOST}}:{{BACKEND_PORT}}/city/{{id}}</h3>
  </div>
</template>

<script>
  import axios from "axios";
  export default {

    asyncData(context) {
      let city,
        country,
        id = context.params.id
        console.log(`http://${process.env.BACKEND_HOST}:${process.env.BACKEND_PORT}/city/${context.params.id}`)
      return axios.get(`http://${process.env.BACKEND_HOST}:${process.env.BACKEND_PORT}/city/${context.params.id}`)
        .then(response => {
          city = response.data
          return axios.get(`http://${process.env.BACKEND_HOST}:${process.env.BACKEND_PORT}/country/${response.data.countryId}`)
        })
        .then(response => {
          country = response.data
          return {
            id,
            city,
            country
          }
        })
    },
    data() {
      return {
        id: this.$route.params.id,
        BACKEND_HOST: process.env.BACKEND_HOST,
        BACKEND_PORT: process.env.BACKEND_PORT
      }
    }
  }

</script>

<style>

</style>
