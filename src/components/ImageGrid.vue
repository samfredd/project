<template>
  <div class="image-grid">
    <div v-for="photo in photos" :key="photo.id" class="image-item" @click="selectPhoto(photo)">
      <!-- Shimmer effect placeholder -->
      <div class="image-placeholder" v-if="!photo.urls.small">
        <div class="shimmer"></div>
      </div>

      <img v-if="photo.urls.small" :src="photo.urls.small" :alt="photo.description" class="image" />

      <div class="overlay">
        <p class="name">{{ photo.user.name }}</p>
        <p class="location" v-if="photo.location?.name">{{ photo.location.name }}</p>
        <p class="location" v-else>Location not available</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['photos'],
  methods: {
    selectPhoto(photo) {
      this.$emit('selectPhoto', photo);
    }
  }
};
</script>

<style scoped>
.image-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 20px;
  position: relative;
  margin-top: -20px; 
}

.image-item {
  position: relative;
  overflow: hidden;
  border-radius: 16px;
  box-shadow: 0 2px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
  height: fit-content;
}

.image-item:nth-child(odd) {
  grid-row: span 2;
}

.image-item:hover {
  transform: scale(1.05);
}

.image-placeholder {
  width: 100%;
  height:  fit-content;
  border-radius: 16px;
  background: #e0e0e0;
  overflow: hidden;
  position: relative;
}

.shimmer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, #e0e0e0 0%, #f0f0f0 50%, #e0e0e0 100%);
  animation: loading 1.5s infinite;
}

@keyframes loading {
  0% {
    transform: translateX(-100%);
  }

  100% {
    transform: translateX(100%);
  }
}

.image {
  width: 100%;
  height: fit-content;
  object-fit: cover;
  border-radius: 16px;
}

.overlay {
  position: absolute;
  bottom: 0;
  background: rgba(0, 0, 0, 0.6);
  color: white;
  padding: 15px;
  text-align: left;
  box-sizing: border-box;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
}

.name {
  font-size: 1.2rem;
  font-weight: bold;
  margin: 0;
}

.location {
  font-size: 0.9rem;
  margin: 5px 0 0;
}
</style>