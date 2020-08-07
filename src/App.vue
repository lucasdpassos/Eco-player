<template>
<v-app 
style="margin 0 auto;">
 <Header />
 <Player />
</v-app> 
</template>

<script>
import Header from './components/Header.vue'
import Player from './components/Player.vue'

export default {
  name: 'App',

  components: {
    Header,
    Player
  },

  data: () => ({
    
  }),
};
</script>
