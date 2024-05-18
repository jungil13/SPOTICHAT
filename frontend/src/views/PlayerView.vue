<template>
    <div>
      <button @click="fetchCurrentlyPlayingTrack">Fetch Currently Playing Track</button>
      <div v-if="currentlyPlayingTrack">
        <h2>Currently Playing Track:</h2>
        <p>{{ currentlyPlayingTrack.name }}</p>
        <p>By: {{ currentlyPlayingTrack.artist }}</p>
        <!-- Add more details as needed -->
      </div>
      <div v-else>
        <p>No track currently playing.</p>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        currentlyPlayingTrack: null
      };
    },
    methods: {
  async fetchCurrentlyPlayingTrack() {
    try {
      const response = await axios.get('/api/currently-playing'); // Make a GET request to your backend endpoint
      this.currentlyPlayingTrack = response.data; // Assuming your backend returns the currently playing track
    } catch (error) {
      console.error('Error fetching currently playing track:', error);
    }
  }
},
mounted() {
  this.fetchCurrentlyPlayingTrack(); // Fetch currently playing track when the component is mounted
}
  };
  </script>
  