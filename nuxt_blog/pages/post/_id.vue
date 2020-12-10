<template>
  <article>
<!--    Im Post detail with id {{ this.$route.params.id }}-->
    <header>
      <h1>{{ post.title }}</h1>
      <p>pub date: {{ post.pub_date }}</p>
      <p class="text-center">
        <img :src="post.img" alt="">
      </p>
    </header>
    <section>
      <p>{{ post.body }}</p>
    </section>
  </article>
</template>

<script>
export default {

  computed: {
    post(){
      let getPost = this.$store.state.post.posts.filter(item => {
        return item.id == this.$route.params.id
      })
      console.log(getPost)
      return getPost[0]
    }
  }
}
</script>
