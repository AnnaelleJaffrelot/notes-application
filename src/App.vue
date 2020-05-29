<template>
  <v-app>
    

    <v-content>
      <Toolbar/>
      
      <Notes/>

    </v-content>
  </v-app>
</template>

<script>
import Notes from './components/Notes';
import Toolbar from './components/Toolbar';

export default {
  name: 'App',

  components: {
    Notes,
    Toolbar,
  },

  data: () => ({
    //
  }),
};
</script>
