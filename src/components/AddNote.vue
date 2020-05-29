<template>
  <form>
    <v-text-field
      v-model="title"
      :error-messages="titleErrors"
      :counter="100"
      label="Titre"
      required
      @input="$v.title.$touch()"
      @blur="$v.title.$touch()"
    ></v-text-field>
    <v-col cols="12" md="6">
      <v-textarea
        v-model="post"
        :error-messages="postErrors"
        solo
        name="post"
        label="Nouvelle note"
        required
        @input="$v.post.$touch()"
        @blur="$v.post.$touch()"
      ></v-textarea>
    </v-col>

    <!--   <v-select
      v-model="select"
      :items="items"
      :error-messages="selectErrors"
      label="Catégorie"
      required
      @change="$v.select.$touch()"
      @blur="$v.select.$touch()"
    ></v-select>-->

    <v-btn class="mr-4" @click="submit">Ajouter la note</v-btn>
    <v-btn @click="clear">Effacer</v-btn>
  </form>
</template>


<script>
import { validationMixin } from "vuelidate";
import { required, maxLength } from "vuelidate/lib/validators";

export default {
  mixins: [validationMixin],

  validations: {
    title: { required, maxLength: maxLength(10) },
    post: { required },
    select: { required }
  },

  data: () => ({
    title: "",
    post: "",
    select: null,
    items: ["Item 1", "Item 2", "Item 3", "Item 4"],
    checkbox: false
  }),

  computed: {
    titleErrors() {
      const errors = [];
      if (!this.$v.title.$dirty) return errors;
      !this.$v.title.maxLength &&
        errors.push("Le titre doit faire moins de 100 caractères");
      !this.$v.title.required && errors.push("Vus devez ajouter un titre");
      return errors;
    },
    postErrors() {
      const errors = [];
      if (!this.$v.post.$dirty) return errors;
      !this.$v.post.required && errors.push("Vous devez ajouter une note");
      return errors;
    }
  },
  created() {
    this.postNote();
  },
  methods: {
    postNote() {
      fetch("http://localhost:3000/note", {
        method: "POST",
        body: JSON.stringify({tittle:'tittle', post:'body'})
      })
        .then(response => response.json())
        .then(json => console.log(json))
        .catch(err => {
          console.log(err);
        });
    },
    submit() {
      this.$v.$touch();
    },
    clear() {
      this.$v.$reset();
      this.title = "";
      this.post = "";
      this.select = null;
      this.checkbox = false;
    }

    /*      fetch('http://localhost:3000/note', {
  method: 'POST',
  body: {
    title: 'Roger',
    post: 'test'
  }
})
  .then(response => {
    console.log(response)
  })
  .catch(err => {
    console.log(err)
  }) */
  }
};
</script>