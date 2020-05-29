<template>
  <v-app>
    

    <v-content>
      <Toolbar/>
      <AddNote/>

    </v-content>
  </v-app>
</template>

<script>
import AddNote from './components/AddNote';
import Toolbar from './components/Toolbar';

export default {
  name: 'App',

  components: {
    AddNote,
    Toolbar
  },

  data: () => ({
    //
  }),
};
</script>
