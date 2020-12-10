<template>
  <div class="about">
    <table>
      <thead>
        <tr>
          <th>#</th>
          <th>title</th>
          <th>year</th>
          <th>description</th>
        </tr>
      </thead>
      <tbody>
    <tr v-for="(item, index) in movies" :key= "index">
      <th>{{item._id}}</th>
      <td>{{item.title}}</td>
      <td>{{item.year}}</td>
      <td>{{item.description}}</td>
    </tr>
      </tbody>
    </table>
  </div>
</template>


<script>

import axios from "axios"

export default {
  data(){
    return{
      movies: []
    }
  }, 
  created(){
    this.listarMovies()
  },
  methods: {
    listarMovies(){
      this.axios.get("movies").then((response) => {
        console.log(response.data);
        // this.movies = response.data
      }).catch((e) => {
        console.log("Error " + e);
      })
    }
  }
}
</script>