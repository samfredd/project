<template>
  <div class="search-bar">
    <button class="search-button" @click="search">
      <i class="fas fa-search"></i>
    </button>
    <input type="text" v-model="searchQuery" placeholder="Search for photos" />
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
      this.$emit('search');
    }
  }
};
</script>

<style scoped>
.search-bar {
  display: flex;
  align-items: center;
  margin: 20px auto;
  width: 60%;
  padding: 8px;
  background: rgba(255, 255, 255, 0.8);
  border-radius: 30px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.search-bar input {
  flex: 1;
  padding: 12px 20px;
  border: none;
  border-radius: 30px;
  font-size: 1rem;
  outline: none;
}

.search-bar input::placeholder {
  color: #aaa;
}

.search-button {
  background: transparent;
  border: none;
  border-radius: 30px;
  color: white;
  padding: 10px 15px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s;
}

.search-button:hover {
  background: transparent;
}

.search-button i {
  margin-right: 5px;
}
</style>