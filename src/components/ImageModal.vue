<template>
  <div class="modal" @click="closeModal">
    <div class="modal-content" @click.stop>
      <!-- Close Button -->
      <button class="close-btn" @click="closeModal">&times;</button>

      <!-- Navigation Arrows positioned at the edges -->
      <button class="nav-arrow left-arrow" @click="prevPhoto" :disabled="isFirstPhoto">&langle;</button>
      <button class="nav-arrow right-arrow" @click="nextPhoto" :disabled="isLastPhoto">&rangle;</button>



      <div class="modal-image">
        <img :src="currentPhoto.urls.full" :alt="currentPhoto.description" />
      </div>
      <div class="modal-header">
        <div class="user-info">
          <p class="user-name">{{ currentPhoto.user.name }}</p>
          <p class="user-location">{{ currentPhoto.location?.name || 'Location not available' }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['photo', 'photos'],
  data() {
    return {
      currentIndex: this.photos.findIndex(p => p.id === this.photo.id),
    };
  },
  computed: {
    currentPhoto() {
      return this.photos[this.currentIndex];
    },
    isFirstPhoto() {
      return this.currentIndex === 0;
    },
    isLastPhoto() {
      return this.currentIndex === this.photos.length - 1;
    },
  },
  methods: {
    closeModal() {
      this.$emit('closeModal');
    },
    nextPhoto() {
      if (this.currentIndex < this.photos.length - 1) {
        this.currentIndex++;
      }
    },
    prevPhoto() {
      if (this.currentIndex > 0) {
        this.currentIndex--;
      }
    },
  },
};
</script>

<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.85);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.modal-content {
  background: white;
  border-radius: 16px;
  width: 800px;
  /* Fixed width */
  height: 600px;
  /* Fixed height */
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.5);
  position: relative;
  overflow: hidden;
}

.modal-image {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

.modal-image img {
  max-width: 100%;
  max-height: 400px;
  object-fit: contain;
}

.close-btn {
  position: absolute;
  top: 10px;
  right: 20px;
  font-size: 2rem;
  background: none;
  border: none;
  color: #000;
  cursor: pointer;
  z-index: 10;
}

.nav-arrow {
  position: fixed;
  top: 50%;
  transform: translateY(-50%);
  font-size: 3rem;
  background: none;
  border: none;
  color: white;
  cursor: pointer;
  z-index: 5;
  padding: 0 20px;
}

.nav-arrow:disabled {
  color: rgba(255, 255, 255, 0.3);
  cursor: not-allowed;
}

.left-arrow {
  left: 20px;
}

.right-arrow {
  right: 20px;
}

.user-info {
  width: 100%;
  padding: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: rgba(255, 255, 255, 0.9);
}

.user-name {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 5px;
  text-align: center;
}

.user-location {
  font-size: 1rem;
  text-align: center;
  color: gray;
}
</style>
