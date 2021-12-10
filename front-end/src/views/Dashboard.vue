<template>
<div class="dashboard">
  <MyPhotos v-if="user" />
  <Login v-else />
</div>
</template>

<script>
import MyPhotos from '@/components/MyPhotos.vue';
import Login from '@/components/Login.vue';
import axios from 'axios';
export default {
  name: 'dashboard',
  components: {
    MyPhotos,
    Login,
  },
  async mounted() {
    try {
      let response = await axios.get('/api/users');
      this.$root.$data.clickCount = response.data.clickCount;
    } catch (error) {
      this.$root.$data.user = null;
    }
  },
  computed: {
    user() {
      return this.$root.$data.user;
    }
  }
}
</script>

<style scoped>
.dashboard {
  padding-top: 10px;
}
</style>

