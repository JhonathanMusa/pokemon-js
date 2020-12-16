<template>
  <div class="about">
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">title</th>
          <th scope="col">year</th>
          <th scope="col">description</th>
          <th scope="col">genre</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in movies" :key="index">
          <th scope="row">{{ item._id }}</th>
          <td>{{ item.title }}</td>
          <td>{{ item.year }}</td>
          <td>{{ item.description }}</td>
          <td>{{ item.genre }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      movies: [],
    };
  },
  created() {
    this.listarMovies();
  },
  methods: {
    listarMovies() {
      this.axios
        .get("movies")
        .then((response) => {
          console.log(response.data.movies);
          this.movies = response.data;
        })
        .catch((e) => {
          console.log("Error " + e);
        });
    },
  },
};
</script>
