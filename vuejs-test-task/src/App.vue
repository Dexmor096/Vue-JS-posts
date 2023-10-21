<template>
  <div class='app'>
    <div class='app__btns'>
      <my-button @click="show">Создать пост</my-button>
       <my-select 
        :options='sortOptions'  
        v-model='selectedSort'
       ></my-select><!--передаем пропс SortOption который будет приниматься как option, связываем через v-model с моделью -->
    </div>
    <my-popup v-model:showPopup='popupVisible'>
      <PostForm @create='createPost'/>
    </my-popup>
  <PostList :posts='posts' @remove='deletePost'/>
</div>
</template>

<script>
import PostForm from '@/components/PostForm.vue';
import PostList from '@/components/PostList.vue';
import axios from "axios";
export default {
  components: {
    PostForm, PostList,
  },
  data() {
    return {
      posts: [],
      title: '',
      body: '',
      popupVisible: false,
      selectedSort: '',
      sortOptions: [
        {
          value: "title",
          name: "По названию", 
        }
        , {
          value: "body",
          name: "По описанию", 
        }
      ],

    }
  },
  methods: {
    
    createPost(post) {
      this.posts.push(post);
      this.popupVisible = false;
    },
    deletePost(post) {
      this.posts = this.posts.filter(elem => elem.id !==post.id)
    },
    show() {
      this.popupVisible = true
    },

      async fetchPosts() {
        try {
           const response = await axios
            .get('https://jsonplaceholder.typicode.com/posts?_limit=10')
            this.posts = response.data;
        } catch (error) {
          console.error(error)
        }
      }
  },
  mounted() {
    this.fetchPosts()
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-size: 18px;
}
.app {
  padding: 50px;
}
.app__btns {
  display: flex;
  margin-top: 10px;
  justify-content: space-between;
}
</style>