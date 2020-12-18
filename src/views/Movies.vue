<template>
  <div class="about">
    <table class="table">
      <thead>
        <tr>
          <!-- <th scope="col">#</th> -->
          <th scope="col">Title</th>
          <th scope="col">Year</th>
          <th scope="col">Description</th>
          <th scope="col">Genre</th>
          <th scope="col">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in movies" :key="index">
          <!-- <th scope="row">{{ item._id }}</th> -->
          <td>{{ item.title }}</td>
          <td>{{ item.year }}</td>
          <td>{{ item.description }}</td>
          <td>{{ item.genre }}</td>
          <td>
            <button class="update">Update</button>
            <button class="delete">Delete</button>
          </td>
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
          this.movies = response.data;
        })
        .catch((e) => {
          console.log("Error " + e);
        });
    },
  },
};
</script>


<style scoped>
th,
td {
  border: none;
  font-family: sans-serif;
}

button {
  border-radius: 5px;
  height: 30px;
  border: none;
}

.update {
  background: #f00;
  color: #fff;
}

.delete {
  background: #f7df2a;
}
</style>