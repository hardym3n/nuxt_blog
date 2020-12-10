<template>
  <article class="card mt-3">
    <img :src="data.img" alt="" class="card-img-top" height="150px">
    <div class="card-body">

      <div class="card-title">
        <h3>
          {{ data.title }}
        </h3>
        <h6 class="card-subtitle text-muted">Category:
          <nuxt-link :to="getLink(getCategory.slug)">{{ getCategory.title }}</nuxt-link>
        </h6>
      </div>
      <div class="card-text">
        <p>{{ data.body.slice(0, 64) }}</p>
      </div>
      <nuxt-link :to="url" class="btn to_post">more</nuxt-link>
    </div>

  </article>
</template>

<style lang="scss">
$btn_bg: #3b8070;
.to_post{
  background: $btn_bg;
  color: #fff;
  border-radius: 10px;
  padding: 5px 25px;
  &:hover{
    color: #fff;
    background: lighten($btn_bg, 20);
  }
}
.card{
  border-color: #eee;
  border-radius: 10px;
  padding: 15px;
  box-shadow: 0px 10px 15px rgba(#000, .05);
  img{
    object-fit: cover;
  }
}
</style>

<script>
import {state} from "~/store/categories";

export default {
  name: 'Card',
  props: {
    data: {
      type: Object
    }
  },
  methods: {
    getLink(slug){
      return '/category/' + slug
    },
  },
  computed: {
    url() {
      return `/post/${this.data.id}`
    },
    getCategory(){
      const category = this.$store.state.categories.categories.filter(el => {
        return el.id == this.data.id
      })
      // console.log(category[0].title)
      return category[0]
    },
  }
}
</script>
