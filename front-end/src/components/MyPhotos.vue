<template>
<div class="main">
  <div class="menu">
    <p><a @click="toggleCredits"><i class="fas fa-dragon"></i></a></p>
    <h2>{{user.firstName}} {{user.lastName}} <a @click="logout"><i class="fas fa-sign-out-alt"></i></a></h2>
    <uploader :show="show" @close="close" @uploadFinished="uploadFinished" />
  </div>
  <p v-if="error">{{error}}</p>
</div>
</template>


<script>
import axios from 'axios';
import Uploader from '@/components/Uploader.vue';

export default {
  name: 'MyPhotos',
  components: {
    Uploader,
    
  },
  data() {
    return {
      show: false,
      photos: [],
      error: '',
    }
  },
  computed: {
    user() {
      return this.$root.$data.user;
    },
  },
  created() {
    this.getPhotos();
  },

  methods: {
    async uploadFinished() {
      this.show = false;
      this.getPhotos();
    },
    close() {
      this.show = false;
    },
    toggleCredits() {
      this.show = true;
    },
    async getPhotos() {
      try {
        this.response = await axios.get("/api/photos");
        this.photos = this.response.data;
      } catch (error) {
        this.error = error.response.data.message;
      }
    },
    async logout() {
      try {
        await axios.delete("/api/users");
        this.$root.$data.user = null;
      } catch (error) {
        this.$root.$data.user = null;
      }
    },
  }
}
</script>

<style scoped>
.menu {
  display: flex;
  justify-content: space-between;
}

.menu h2 {
  font-size: 14px;
}
</style>

