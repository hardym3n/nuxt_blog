<template>
  <div>
    <a @click="goBack" href="">Nazad</a>
  </div>
</template>

<script>
export default {
  name: "Navigator",
  methods: {

    goBack(e) {
      e.preventDefault();
      this.$router.go(-1)
    }

  }
}
</script>

<style scoped>

</style>
