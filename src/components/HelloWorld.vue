<template>
  <v-container>
<Notes/>
<AddNote/>

  </v-container>
</template>

<script>
import Notes from './Notes';
import AddNote from './AddNote';
  export default {
    name: 'HelloWorld',

     components: {
  
    Notes,
    AddNote,

  },

  }
</script>
