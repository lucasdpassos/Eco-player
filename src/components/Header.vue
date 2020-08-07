<template>
  <v-app>
     <v-card class="overflow-hidden">
    <v-toolbar
            
      dark
      prominent
      src='../assets/bg.jpg'      
      style="width: 700px; margin: 0 auto;"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"          
        ></v-img>
      </template>      

      <v-toolbar-title class="display-2">Eco
      <v-subheader>Alimento épico para o cérebro!</v-subheader>
      </v-toolbar-title>       
                   
    </v-toolbar>
    
  </v-card>
  </v-app>
</template>
