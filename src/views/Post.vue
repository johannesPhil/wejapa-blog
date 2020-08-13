<template>
  <div class="post">
    <div class="title">
      <h3>{{ title }}</h3>
    </div>
    <div class="body">
      {{ body }}
    </div>
    <div class="comments">
      <h3 v-if="!nullComment">Comments</h3>
      <div class="comment" v-for="comment in comments" :key="comment.id">
        <p class="comment__body">
          {{ comment.body }}
        </p>
        <p class="comment__user">
          {{ comment.name }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Post',
  data() {
    return {
      title: '',

      body: '',

      comments: [],

      nullComment: false,
    }
  },

  props: ['id'],

  async created() {
    await this.getPost()
    await this.getComment()
  },

  methods: {
    getPost() {
      try {
        fetch('https://jsonplaceholder.typicode.com/posts/' + this.id)
          .then((response) => response.json())

          .then((post) => {
            this.title = post.title

            this.body = post.body

            console.log(this.body)
          })
      } catch (error) {
        console.log(error)
      }
    },

    getComment() {
      try {
        fetch(
          'https://jsonplaceholder.typicode.com/posts/' + this.id + '/comments',
        )
          .then((response) => response.json())

          .then((comment) => {
            this.comments = comment

            if (this.comments.length === 0) {
              nullComment = !nullComment
            }

            console.log(this.comments)
          })
      } catch (error) {
        console.log(error)
      }
    },
  },
}
</script>

<style scoped>
.post {
  padding: 2%;
  margin: 5% auto;
  max-width: 500px;
}

.title {
  text-transform: capitalize;
  text-align: left;
}

.body {
  text-align: left;
  line-height: 1.6rem;
  text-transform: none;
  color: #2c3e50;
  border-radius: 12px;
  box-shadow: 1px 1px 5px 2px #bebebe3d;
  padding: 5%;
}

.body::first-letter,
.comment p::first-letter {
  text-transform: capitalize;
}

.comments {
}

.comments h3 {
  position: relative;
  text-align: left;
}

.comments h3::after {
  display: block;
  content: '';
  position: absolute;

  left: 0;
  width: 100%;
  border-bottom: solid 2px #19bf69;
}

.comment {
  margin: 2% 0;
  border-radius: 12px;
  box-shadow: 1px 1px 5px 2px #bebebe3d;
  padding: 5%;
  background: #19bf69;
  color: #fff;
  text-align: left;
}

.comment__user {
  text-align: right;
  font-style: italic;
  font-weight: bolder;
}
</style>
