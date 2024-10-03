<template>
  <div class="search-bar">
    <input type="text" v-model="searchQuery" placeholder="Search for photos" />
    <button class="search-button" @click="search">
      <i class="fas fa-search"></i> <!-- Search icon -->
    </button>
  </div>
</template>

<script>
export default {
  props: ['modelValue'],
  computed: {
    searchQuery: {
      get() {
        return this.modelValue;
      },
      set(value) {
        this.$emit('update:modelValue', value);
      }
    }
  },
  methods: {
    search() {
      this.$emit('search'); // Emit search event when the button is clicked
    }
  }
};
</script>

<style scoped>
.search-bar {
  display: flex;
  /* Use flexbox for alignment */
  align-items: center;
  /* Center items vertically */
  margin: 20px auto;
  width: 60%;
  padding: 8px;
  /* Add some padding */
  background: rgba(255, 255, 255, 0.8);
  /* Slightly transparent background */
  border-radius: 30px;
  /* Rounded corners */
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  /* Soft shadow for depth */
}

.search-bar input {
  flex: 1;
  /* Allow input to take remaining space */
  padding: 12px 20px;
  /* Add padding to input */
  border: none;
  /* Remove default border */
  border-radius: 30px;
  /* Match the border radius of the container */
  font-size: 1rem;
  /* Font size */
  outline: none;
  /* Remove outline on focus */
}

.search-bar input::placeholder {
  color: #aaa;
  /* Placeholder color */
}

.search-button {
  background: #007bff;
  /* Primary button color */
  border: none;
  /* Remove default border */
  border-radius: 30px;
  /* Match the border radius */
  color: white;
  /* Text color */
  padding: 10px 15px;
  /* Padding for button */
  cursor: pointer;
  /* Pointer cursor on hover */
  font-size: 1rem;
  /* Font size */
  transition: background-color 0.3s;
  /* Smooth transition for hover effect */
}

.search-button:hover {
  background: #0056b3;
  /* Darker shade on hover */
}

.search-button i {
  margin-right: 5px;
  /* Space between icon and text */
}
</style>
