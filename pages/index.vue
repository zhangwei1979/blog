<template>
  <div class="home-page">
    <section class="intro">
      <h1>Get teh laest tech news!</h1>
    </section>
    <!-- <section class="featured-posts"> -->
      <PostList :posts="loadedPosts"/>
    <!-- </section> -->
  </div>
</template>

<script>
import PostList from '@/components/Posts/PostList'

export default {
  components : {
    PostList
  },
  /*asyncData(context, callback) {
      setTimeout(()=> {
        callback(null, {loadedPosts: [
          {id:"1", title:"my first title", previewText:"My first preview", thumbnail:"https://miro.medium.com/max/2000/0*kBHpKva09AsGj7RQ"},
          {id:"2", title:"my second title", previewText:"My second preview", thumbnail:"https://miro.medium.com/max/2000/0*kBHpKva09AsGj7RQ"}
        ]})
    })
  }*/
  computed: {
      loadedPosts() {
        console.log("================/index.vue computed loadedPosts=====")
        return this.$store.getters.loadedPosts
      }
    }
  /* ,data() {
    return {
      loadedPosts: [
      {id:"1", title:"my first title", previewText:"My first preview", thumbnail:"https://miro.medium.com/max/2000/0*kBHpKva09AsGj7RQ"},
      {id:"2", title:"my second title", previewText:"My second preview", thumbnail:"https://miro.medium.com/max/2000/0*kBHpKva09AsGj7RQ"}
      ]
    }
  }*/
}
  
</script>


<style scoped>
  .intro {
  height: 300px;
  position: relative;
  padding: 30px;
  box-sizing: border-box;
  background-position: center;
  background-size: cover;
  background-image:url('~assets/images/main-page-background.jpg')
}

.intro h1 {
  position: absolute;
  top: 10%;
  left: 5%;
  width: 90%;
  font-size: 1.5rem;
  color: black;
  background-color: rgb(211, 211, 211);
  padding: 10px;
  border-radius: 10px;
  box-shadow: 3px 3px 3px black;
  box-sizing: border-box;
  border: 1px solid black;
}

@media (min-width: 768px) {
  .intro h1 {
    font-size: 2rem;
  }
}

.featured-posts {
  display: flex;
  padding: 20px;
  box-sizing: border-box;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
}

</style>


