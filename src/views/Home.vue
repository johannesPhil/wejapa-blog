<template>
  <div class="home">
    <div class="posts-container">
      <h2>Posts</h2>
      <div class="posts">
        <router-link
          :to="{ name: 'Post', params: { id: post.id } }"
          v-for="post in posts"
          :key="post.id"
          class="link"
        >
          <div class="post">
            {{ post.title }}
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {},

  data() {
    return {
      posts: [],
    }
  },

  created() {
    fetch('https://jsonplaceholder.typicode.com/todos/')
      .then((response) => response.json())

      .then((data) => {
        this.posts = data
        console.log(data)
      })
  },
}
</script>

<style scoped>
.posts-container {
  padding: 2% 5%;
}

h2 {
  text-align: left;
  position: relative;
}

h2::after {
  display: block;
  content: '';
  position: absolute;
  left: 0;
  width: 50%;
  border-bottom: solid 2px #19bf69;
}

.posts {
  width: 100%;
  height: auto;

  display: flex;
  flex-flow: row wrap;
  justify-content: space-between;
}

.link {
  color: #2c3e50;
  text-decoration: none;
  border-left: solid 2px #19bf69;
  /* background: #19bf6913; */
  margin: 2% 0;
  transition: ease-in-out 200ms;
}

.link:hover {
  /* background: #19bf69; */
  color: #19bf69;
  border-radius: 5px;
  box-shadow: 1px 1px 5px 2px #bebebe3d;
  transform: scale(1.1);
}

.post {
  width: 300px;
  min-height: 30px;
  padding: 1rem;
  margin: 1rem;
  text-align: left;
  text-transform: capitalize;
}
</style>
