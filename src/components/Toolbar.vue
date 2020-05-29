<template>
<v-container class="pa-0">
  <v-card
    color="grey lighten-4"
    flat
    tile
  >
    <v-toolbar >
 

      <v-toolbar-title>Notes</v-toolbar-title>

      <v-spacer></v-spacer>

      

        <v-app-bar-nav-icon  @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        
    </v-toolbar>
</v-card>
      <v-navigation-drawer
      v-model="drawer"
      absolute
      temporary
    >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title>Notes</v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense>

        <v-list-item
          v-for="item in items"
          :key="item.title"
          link
        >

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  

</v-container>
</template>


<script>
export default {
 data() {
       return {
        drawer: null,
        items: [
          { title: 'Ajouter une note' },
          { title: 'Toutes les notes' },
        ],
       }
    }
}
</script>

<style>

</style>