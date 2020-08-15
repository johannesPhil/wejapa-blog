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
      <div class="form-container">
        <form action="" @submit.prevent="addComment">
          <div class="form__control">
            <label for="name" class="form__el">
              Your name
              <i>(required)</i>
            </label>
            <input
              type="text"
              name="name"
              id="name"
              class="form__el"
              required
              v-model="newComment.name"
            />
            <label for="mail" class="form__el">
              Your Mail
              <i>(required)</i>
              )
            </label>
            <input
              type="email"
              name="mail"
              id="mail"
              class="form__el"
              required
              v-model="newComment.email"
            />
            <label for="comment" class="form__el">
              Add Comment
              <i>(required)</i>
            </label>
            <textarea
              required
              name="comment"
              id="comment"
              cols="30"
              rows="10"
              class="form__el"
              v-model="newComment.body"
            ></textarea>
          </div>
          <button type="submit" class="form__el">Add Comment</button>
        </form>
      </div>
      <div class="comment" v-for="comment in comments" :key="comment.id">
        <p class="comment__body">
          {{ comment.body }}
        </p>
        <p class="comment__email">
          {{ comment.email }}
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

      comments: {},

      nullComment: false,

      newComment: {
        name: '',
        email: '',
        body: '',
      },
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
        fetch('')
        console.log(error)
      }
    },

    addComment() {
      //Mimic adding a resource

      if (this.newComment.email && this.newComment.body) {
        console.log(this.newComment.mail)
        console.log(this.newComment)

        this.comments.push(this.newComment)
      }
      this.newComment = {
        email: '',
        body: '',
      }

      // fetch(
      //   'https://jsonplaceholder.typicode.com/posts/' + this.id + '/comments',
      //   {
      //     method: 'POST',
      //     body: JSON.stringify(this.comment),
      //   },
      // ).then((response) => {
      //   response.json()
      //   if (response.status === 201) {
      //     //temporarily add the comment

      //     if (this.comment.mail && this.comment.message) {
      //       console.log(this.comment.mail)
      //       console.log(this.comment.message)

      //       this.comments.push(this.comment)
      //     }
      //     alert('Your comment has been added')
      //     this.comments.push(this.comment)
      //   }
      // })
      // .then((response) => {
      //   alert(response)
      //   console.log(response)
      // })
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

.form-container {
  width: 100%;
}
.form__el {
  display: block;
  width: 100%;
  margin: 0.5rem auto;
  padding: 0.5rem;
  outline: none;
}

label.form__el {
  text-align: left;
}

input.form__el {
  height: 2rem;
  border-radius: 5px;
  border: solid 1px #ccc;
}

textarea.form__el {
  border-radius: 5px;
  outline: none;
  transition: ease-in-out 200ms;
}

input:active,
input:hover,
textarea.form__el:hover,
textarea.form__el:active {
  box-shadow: 1px 1px 5px 2px #8f91902d;
}

button.form__el {
  width: 30%;
  margin: auto 70%;
  background: #19bf69;
  height: 2.5rem;
  border: none;
  border-radius: 5px;
  font-size: 1rem;
  color: #fff;
  transition: ease-in 200ms;
}

button.form__el:hover {
  background: #fff;
  color: #19bf69;
  box-shadow: 1px 1px 5px 2px #bebebe3d;
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

.comment__email {
  text-align: right;
  font-style: italic;
  font-weight: bolder;
}
</style>
