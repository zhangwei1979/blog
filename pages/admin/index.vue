<template>
  <div class="adim-page">
    <section class="new-post">
      <AppButton @click="$router.push('/admin/new-post')">Create Post</AppButton>
    </section>
    <section class="existing-posts">
      <h1>Existing Posts</h1>
      <!-- <PostList :is-admin="true"/> -->
      <PostList isAdmin :posts="loadedPosts"/>
    </section>
  </div>
</template>
<script>
import PostList from '@/components/Posts/PostList'
import AppButton from '@/components/UI/AppButton'

export default {
  //middleware:'auth',
  components : {
    PostList,
    AppButton
  },
  /*
  asyncData(context, callback) {
      setTimeout(()=> {
        callback(null, {loadedPosts: [
          {id:"1", title:"my first title", previewText:"My first preview", thumbnail:"https://miro.medium.com/max/2000/0*kBHpKva09AsGj7RQ"},
          {id:"2", title:"my second title", previewText:"My second preview", thumbnail:"https://miro.medium.com/max/2000/0*kBHpKva09AsGj7RQ"}
        ]})
    })
  }
  */
  computed: {
      loadedPosts() {
        console.log("================33=====")
        return this.$store.getters.loadedPosts
      }
    }
}
  
</script>

<style scoped>
.admin-page {
  padding: 20px;
}

.new-post {
  text-align: center;
  border-bottom: 2px solid #ccc;
  padding-bottom: 10px;
}

.existing-posts h1 {
  text-align: center;
}
</style>