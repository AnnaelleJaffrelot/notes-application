<template>
  <div>
    <v-tabs background-color="red lighten-3" class="elevation-0" dark>
      <v-tabs-slider></v-tabs-slider>
      <v-tab>Notes</v-tab>
      <v-tab-item>
        <v-container class="spacing-playground py-0 px-0" fluid fill-height>
          <v-card flat tile elevation="0">
            <v-card-text>
              <h2 class="mb-5">Toutes les notes</h2>

              <!--              <li v-for="note in notes">
   {{note}}
              </li>-->

              <v-expansion-panels>
                <v-expansion-panel cols="sm" sm="12" v-for="(note,i) in notes" :key="i">
                  <v-expansion-panel-header>{{note.title}}</v-expansion-panel-header>
                  <v-expansion-panel-content>
                    {{note.post}}
                    <div class="my-2">
                      <v-btn small color="red lighten-3">Supprimer</v-btn>
                    </div>
                  </v-expansion-panel-content>
                </v-expansion-panel>
              </v-expansion-panels>
            </v-card-text>
          </v-card>
        </v-container>
      </v-tab-item>
      <v-tab>Ajouter une note</v-tab>

      <v-tab-item>
        <v-card flat tile>
          <v-card-text>
            <h2 class="mb-6 mt-2">Ajouter une nouvelle note</h2>
            <AddNote />
          </v-card-text>
        </v-card>
      </v-tab-item>
    </v-tabs>
  </div>
</template>

<script>
import AddNote from "./AddNote";
export default {
  data() {
    return {
      notes: ""
    };
  },
  name: "Notes",

  created() {
    this.getNotes();
  },
  methods: {
    getNotes() {
      /* https://jaffrelot-notes-api.herokuapp.com/notes */
      /* http://localhost:3000/notes */
      fetch("https://jaffrelot-notes-api.herokuapp.com/notes", {
        method: "GET"
      })
        .then(response => {
          return response.json();
        })
        .then(response => {
          this.notes = response;
        })
        .catch(err => {
          console.log(err);
        });
    }
  },

  components: {
    AddNote
  }
  /* fetch("http://localhost:3000/notes").then(response=>response.json()).then(response=>console.log(response)) */
};
</script>

<style>
</style>