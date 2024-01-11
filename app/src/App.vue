<template>
  <v-app>
    <v-main>
      
        <v-card>
          <v-tabs
            v-model="tab"
            bg-color="indigo"
          >
            <v-tab value="results">Results</v-tab>
            <v-tab value="people">Vote</v-tab>
            <v-tab value="create">Add new Person</v-tab>
          </v-tabs>
      
          <v-card-text>
            <v-window v-model="tab">
              <v-window-item value="results">
                <Results/>
              </v-window-item>
              
              <v-window-item value="people">
                <Vote/>
              </v-window-item>
    
              <v-window-item value="create">
                <CreatePerson/>
              </v-window-item>
            </v-window>
          </v-card-text>
        </v-card>
     
    </v-main>
  </v-app>
</template>

<script>


  
  export default {
    data: () => ({
        tab: null,
    }),
    components: {  }
}

</script>
