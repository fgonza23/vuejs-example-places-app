<template>
  <div class="home">
    <h1>Places</h1>

    <div>
      Name: <input v-model="newPlace.name">
      Address: <input v-model="newPlace.address">
      <button @click="addPlace()">Add Place</button>
    </div>
  </div>
</template>

<style>
</style>

<script>
  var axios = require('axios');

export default {
  data: function() {
    return {
      places: [],
      newPlace: {name: "", address: ""}
    };
  },
  created: function() {
    axios
    .get("http://localhost:3000/api/places")
    .then(response => {
      this.places = response.data;
    });
  },
  methods: {
    addPlace: function() {
      var params = {
                    name: this.newPlace.name,
                    address: this.newPlace.address
                    };
    axios
    .post("http://localhost:3000/api/places", params)

    // axios
    // .post("http://localhost:api/places", params)
    // .then(function(response) {
    //   this.places.push(response.data);
    // }.bind(this));
  },
  computed: {}
};
</script>