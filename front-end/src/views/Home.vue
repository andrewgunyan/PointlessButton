<template>
<div class="home">
  <div class = "help">
      <h1 id = "black"> Times Clicked: {{length}}</h1>
    </div>
      <div class = "button">
      <button @click = "IncrementCount" class="center">Click!</button>
    </div>
    <div class = "button">
          <button @click = "updateClicks(name, length)" class = "smallCenter">Save</button>
</div>
</div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'Home',
  components: {
  },
  data() {
    return {
      photos: [],
      error: '',
    }
  },
  created() {
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
    name() {
      return this.$root.$data.user.username
    },
    length() {
      return this.$root.$data.clickCount
    }
  },
  methods: {
    async getClicks() {
      try {
        let response = await axios.get("/api/users");
        console.log(response)
        this.$root.$data.clickCount = response.data.user;
      } catch (error) {
        this.error = error.response.data.message;
      }
    },

    async updateClicks(current_user, test) {
      try {
        console.log(current_user);
        console.log(test)
        await axios.put("/api/users/" + current_user, {
          username: current_user,
          clickCount: test,
        });

      } catch (error) {
        console.log(error);
      }
    },

    IncrementCount() {
      this.$root.$data.clickCount++
    }
  }


}
</script>