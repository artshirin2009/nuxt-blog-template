<template>
  <div>
    <v-card max-width="500" class="mx-auto">
      <v-list light>
        <v-list-group v-for="item in countries" :key="item.title" v-model="item.active" no-action>
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title v-text="item.title"></v-list-item-title>
            </v-list-item-content>
          </template>

          <v-list-item v-for="subItem in item.cities" :key="subItem.title">
            <v-list-item-content>
              <v-list-item-title v-text="subItem.title" @click="goToCity(subItem)"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
      </v-list>
    </v-card>
  </div>


</template>
<script>
  import axios from "axios";
  export default {
    props: ['countries'],
    data() {
      return {
        name: "SelectCountry"
      }
    },
    methods: {
      goToCity(subItem) {
        this.$router.push(`/city/${subItem.id}`)
      }

    },
    mounted() {

    }

  }

</script>
