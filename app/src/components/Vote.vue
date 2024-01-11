<!-- Vote.vue -->
<template>
    <div>
      <h2>List of Persons</h2>
      <br>
      <ul>
        <li v-for="person in persons" :key="person.id">
            <v-card color="indigo" variant="tonal">
          <v-card-item>
            <div>
            
              <h2>
                {{ person.name}}
              </h2>
              <div >{{ person.email}}</div>
            </div>
          </v-card-item>

          <v-card-actions>
            <v-btn @click="vote(person.id)">Vote</v-btn>
          </v-card-actions>
        </v-card>
         <br>
          
        </li>
      </ul>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue'
  import axios from 'axios'
  
  const persons = ref([])
  
  onMounted(async () => {
    try {
      const response = await axios.get('http://localhost:8000/persons')
      persons.value = response.data
    } catch (error) {
      console.error(error)
    }
  })
  
  const vote = async (personId) => {
    try {
        const person = persons.value.find(p => p.id === personId)
        const response = await axios.post('http://localhost:8000/vote', person)
    
      console.log(response.data)
    } catch (error) {
      console.error(error)
    }
  }
  </script>
  