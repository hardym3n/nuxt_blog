<template>
  <div>
    <Card class="col-12" v-for="item in posts" :key="item.id" :data="item"></Card>
  </div>
</template>

<script>
import Card from '@/components/card/Card.vue'

export default {
  components: {
    Card
  },
  computed: {
    posts(){
      return this.$store.state.post.posts
    }
  }
}
</script>

<style lang="scss">

</style>
