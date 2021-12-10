<template>
<div class="leaderboard">
  <section class="rankings">
    <div class="rank" v-for="user in users" :key="user.id">
      <div class = "grid">
      <h2 class = "left">{{user.username}}</h2><h2 class = "right">{{user.numClicks}}</h2>
      </div><hr>
    </div>
  </section>
</div>

</template>
<script>
import axios from 'axios';
export default {
    name: 'Leaderboard',
        data() {
            return {
                users: [],
            }
        },
        created() {
            this.getUsers();
        },
        methods: {
        async getUsers() {
          try {
            let response = await axios.get('/api/users/all');
            this.users = response.data;
            return true;
        } catch (error) {
            console.log(error);
        }
    }
}
    
}

</script>

<style scoped>

.grid {
  display: grid;
  grid-auto-flow: column;
}

.rankings {
  align-items: center;
  color: black;
  font-size: 45px;
  justify-content: center;
  text-align: center;
  padding-top: 150px;
}

.left {
  font-size: 45px;
  text-align: left;
  justify-content: left;
}

.right {
  font-size: 45px;
  text-align: right;
  justify-content: right;
  align-items: right;
}

.image h2 {
  font-style: italic;
}

/* Masonry */
*,
*:before,
*:after {
  box-sizing: inherit;
}

.image-gallery {
  column-gap: 1.5em;
}

.image {
  margin: 0 0 1.5em;
  display: inline-block;
  width: 100%;
  margin-top: 100px;
}

.image img {
  width: 100%;
}

/* Masonry on large screens */
@media only screen and (min-width: 1024px) {
  .image-gallery {
    column-count: 4;
  }
}

/* Masonry on medium-sized screens */
@media only screen and (max-width: 1023px) and (min-width: 768px) {
  .image-gallery {
    column-count: 3;
  }
}

/* Masonry on small screens */
@media only screen and (max-width: 767px) and (min-width: 540px) {
  .image-gallery {
    column-count: 2;
  }
}
</style>

