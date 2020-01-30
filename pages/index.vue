<template>
  <v-overlay :value="overlay">
    <SelectCountry :countries='countries'/>
  </v-overlay>
</template>

<script>
import axios from "axios";
  import SelectCountry from '~/components/SelectCountry.vue'

  export default {
     asyncData() {
      
      return  axios.get("http://localhost:3000/country")
      
      .then(response => {
          return {countries : response.data}
          countries[0].active = true
        })
      
    },
    data: () => ({
      overlay: true,
    }),
    components: {
      SelectCountry
    }
  }

</script>

<style>
  .container {
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }

  .title {
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
      'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    display: block;
    font-weight: 300;
    font-size: 100px;
    color: #35495e;
    letter-spacing: 1px;
  }

  .subtitle {
    font-weight: 300;
    font-size: 42px;
    color: #526488;
    word-spacing: 5px;
    padding-bottom: 15px;
  }

  .links {
    padding-top: 15px;
  }

</style>
