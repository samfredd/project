<template>
  <div id="app">
    <!-- Conditionally render App Bar based on search query -->
    <div v-if="searchQuery" class="app-bar">
      <button class="back-button" @click="goBack">
        <i class="fas fa-arrow-left"></i> <!-- Back arrow icon -->
      </button>
      <h1 class="app-title">Search Results for "{{ searchQuery }}"</h1>
    </div>

    <SearchBar v-model="searchQuery" @search="fetchPhotos" />

    <!-- Show shimmer effect while loading photos -->
    <div v-if="isLoading">
      <ShimmerLoader />
    </div>

    <!-- Show images when not loading -->
    <ImageGrid v-else :photos="photos" @selectPhoto="selectPhoto" />

    <ImageModal v-if="showModal" :photo="selectedPhoto" :photos="photos" @closeModal="showModal = false" />
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import ImageGrid from './components/ImageGrid.vue';
import ImageModal from './components/ImageModal.vue';
import ShimmerLoader from './components/ShimmerLoader.vue'; // Import ShimmerLoader

export default {
  components: {
    SearchBar,
    ImageGrid,
    ImageModal,
    ShimmerLoader // Register the ShimmerLoader component
  },
  data() {
    return {
      searchQuery: '',
      photos: [],
      selectedPhoto: null,
      showModal: false,
      isLoading: false, // Loading state
    };
  },
  mounted() {
    this.fetchPhotos(); // Fetch random photos when the component is mounted
  },
  methods: {
    fetchPhotos() {
      const UNSPLASH_API_KEY = process.env.VUE_APP_UNSPLASH_ACCESS_KEY;
      this.isLoading = true; // Set loading to true

      // Check if searching or fetching random photos
      if (this.searchQuery) {
        // Fetch search results
        axios
          .get(`https://api.unsplash.com/search/photos`, {
            params: { query: this.searchQuery, client_id: UNSPLASH_API_KEY }
          })
          .then(response => {
            this.photos = response.data.results;
          })
          .catch(error => {
            console.error("Error fetching photos: ", error);
          })
          .finally(() => {
            this.isLoading = false; // Set loading to false after fetching
          });
      } else {
        // Fetch random photos for the homepage
        axios
          .get(`https://api.unsplash.com/photos/random`, {
            params: { count: 10, client_id: UNSPLASH_API_KEY } // Fetch 10 random photos
          })
          .then(response => {
            this.photos = response.data;
          })
          .catch(error => {
            console.error("Error fetching random photos: ", error);
          })
          .finally(() => {
            this.isLoading = false; // Set loading to false after fetching
          });
      }
    },
    selectPhoto(photo) {
      this.selectedPhoto = photo;
      this.showModal = true;
    },
    goBack() {
      this.searchQuery = ''; // Reset search query to go back to homepage
      this.photos = []; // Clear photos
      this.showModal = false; // Close any open modal
      this.fetchPhotos(); // Fetch random photos again
    },
  },
};
</script>

<style scoped>
.app-bar {
  position: sticky;
  top: 0;
  background-color: rgba(255, 255, 255, 0.9);
  padding: 10px 20px;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  display: flex;
  align-items: center;
}

.back-button {
  background: none;
  border: none;
  cursor: pointer;
  font-size: 1.5rem;
}

.app-title {
  margin-left: 10px;
  font-size: 1.5rem;
}
</style>
