<template>
<div class="container">
      <p>
        <button 
          v-if="!isOpenComments"
          @click="loadComment"
          class="btn primary"
        >
          Загрузить комментарии
        </button>
      </p>
      <div v-if="isOpenComments" class="card">

        <h2>Комментарии</h2>

        <ul
          v-for="comment in comments" :key="comment"
          class="list"
        >
          <li class="list-item">
            <div>
              <p><strong>{{comment.email}}</strong></p>
              <small>{{comment.body}}</small>
            </div>
          </li>
        </ul>

      </div>

      <div
        v-if="loading"
        class="loader"
      >
      </div>
      
    </div>
</template>

<script>
import axios from 'axios'

  export default {
    name: 'App-comments',
    data () {
      return {
        loading: false,
        isOpenComments: false,
        comments: []
      }
    },
    methods: {
      async loadComment () {
        try {
          this.loading = true;
          const response = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=10');  
          console.log(response.data);
          this.comments = Object.keys(response.data).map(key => {
            return {
              email: response.data[key].email,
              body: response.data[key].body
            }
          });

          this.loading = false;
          console.log(this.comments);

          this.isOpenComments = true;

        } catch(error) {
            alert('Произошла ошибка, попробуйте позже');
            console.log(error.message);
            this.loading = false;
        }
      }
    }    
  }
</script>

<style>

</style>