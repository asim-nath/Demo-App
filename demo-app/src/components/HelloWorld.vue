<template>
  <v-container>
    <v-container>
    <v-text-field label="Search Name of Movies" v-model="name"></v-text-field>
    <v-btn primary @click="getData()">Search</v-btn>
    </v-container>
    <v-container>
      <v-row>
      <v-card 
      v-for = "(m,i) in movies"
      :key = i
    class="mx-auto ma-4"
    max-width="400"
  >
    <v-card-title>{{m.title}}</v-card-title>
    <v-card-text class="text--primary">
      <div>{{m.original_language}}</div>
    </v-card-text>
  </v-card>
  </v-row>
    </v-container>
  </v-container>
</template>

<script>
import axios from 'axios';
  export default {
    name: 'HelloWorld',

    data: () => ({
      name: '',
      movies:[]
    }),
    methods:{
     async getData(){

        let moviedata = await axios.get(`https://api.themoviedb.org/3/search/movie?api_key=ecae46a93605db6f6aec6ad449d5cef2&query=${this.name}`);
        this.movies = moviedata.data.results;
      }
    }
  }
</script>
