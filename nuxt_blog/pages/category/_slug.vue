<template>
  <div>
    <p>Posts by Category {{ postsByCat.title }}</p>
    <Card class="col-12" v-for="item in postsByCat.posts" :key="item.id" :data="item"></Card>
    <h2></h2>
  </div>
</template>

<script>
export default {
  name: "_id.vue",
  computed: {
    postsByCat(){
      const slug = this.$route.params.slug
      const category = this.$store.state.categories.categories.filter(el => {
        return el.slug == slug
      })
      const posts = this.$store.state.post.posts.filter(el => {
        return el.category == category[0].id
      })
      // console.log(data)
      return {
        'title': category[0].title,
        'posts': posts,
      }
    }
  }
}
</script>

<style scoped>

</style>
