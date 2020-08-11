<template>
  <div class="index">
    <h1>{{ message }}</h1>
    <h2> See below toys! </h2>
    <div v-for="toy in toys">
      <p>Name: {{toy.name}} </p>
      <p>Size: {{toy.size}} </p>
      <p>Image Url: {{toy.image_url}}</p>
    </div>

  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      message: "Welcome to the Index page",
      toys: []
    };
  },
  created: function() {
    this.indexToys();
  },
  methods: {
    indexToys: function() {
      console.log("this is the index page...")

      axios.get("/api/toys").then(response => {
        console.log(response.data);
        this.toys = response.data;
      });
    }
  }
};
</script>