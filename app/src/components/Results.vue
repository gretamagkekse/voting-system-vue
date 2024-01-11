<!-- Results.vue -->
<template>
    <div>
      <h2>List of Votes</h2>
      <br>
      <ul>
        <li v-for="vote in votes" :key="vote.id">
          <v-card color="indigo" variant="tonal">
          <v-card-item>
            <div>
            
              <h2>
                {{ vote.person.name}}
              </h2>
              <br>
              <div >Stimmen: {{ vote.Stimmzahl}}</div>
            </div>
          </v-card-item>

          
        </v-card>
          <br>
        </li>
      </ul>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue'
  import axios from 'axios'
  
  const votes = ref([])
  
  onMounted(async () => {
    try {
      const response = await axios.get('http://localhost:8000/vote')
      votes.value = response.data
      console.log(votes.value)
    } catch (error) {
      console.error(error)
    }
  })
  </script>
  