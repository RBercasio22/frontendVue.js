<template>

  <v-app class="v-app">
    
    <!-- <v-main >
      <router-view />
    </v-main> -->
    <!-- for ROW -->
    <!-- class="bg-grey-lighten-5 d-sm-flex justify-center" 
    align="center" -->
    <v-row no-gutters class="fill-height">
      <v-col cols="12" sm="6"> 
        <v-card>
          <!-- <HelloWorld /> -->
        </v-card>
      </v-col>

      <v-col cols="12" sm="6">
        <router-view />
      </v-col>
    </v-row>
  
  </v-app>

</template>


<style>


.v-app {
  height: 100%;
  background-color: green;
}

/* html, body, #app {
  height: 100%;
}

v-app {
  height: 100%;
}
.router-view {
  overflow: hidden;
} 
html, body, #app {
  margin: 0;
  padding: 0;
  overflow-x: hidden; /* This prevents horizontal scroll
  
  
  */

  


</style>

<script setup>
  //
</script>
