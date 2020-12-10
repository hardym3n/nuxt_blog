<template>
    <nav class="row navbar align-items-start">
      <div class="logo col-12 text-center">
        <h2>
          Open | Blog
        </h2>
      </div>
      <div class="navbar__menu col-12">
        <ul class="menu__list" v-if="getMenu">
          <li class="menu__item" v-for="item in getMenu" :key="item.id">
            <nuxt-link class="menu__link" :to="setUrl(item.slug)">{{ item.title }}</nuxt-link>
          </li>
        </ul>
      </div>
    </nav>
</template>

<script>
export default {
  name: "Navbar",
  methods: {
    setUrl(id) {
      return `/category/${id}`
    }
  },
  computed: {
    getMenu(){
      return this.$store.state.categories.categories
    },
  },

}
</script>

<style lang="scss">
.logo{
  padding: 15px;
}
.navbar{
  //display: flex;
  //flex-direction: row;
  //justify-content: space-between;
  background: #ffffff;
  min-height: 100vh;
  position: sticky;
  top: 0;
  border: 1px solid #eee;
}
.menu__list{
  //display: flex;
  list-style: none;
  padding: 0;
}
.menu__item{
  padding: 0;
  margin: 0;
  text-transform: uppercase;
}
.menu__link{
  //color: #fff;
  color: #35495e;
  padding: 15px;
  display: block;
  text-decoration: none;
  border-bottom: 1px solid rgba(0, 0, 0, 0);
  transition: .5s;
  &.nuxt-link-active{
    //text-decoration: underline;
    //border-bottom: 1px solid #3b8070;
    background: #3b8070;
    color: #fff;
  }
}
</style>
