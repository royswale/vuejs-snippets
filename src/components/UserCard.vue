<template>
  <div class="user">
    <h2 v-text="name"></h2>
    <p v-text="email"></p>
  </div>
</template>

<script>
export default {
  name: 'UserCard',
  props: {
    name: String,
    email: String
  }
}
</script>

<style lang="scss" scoped>
.user {
  text-align: left;

  h2 {
    font-size: 1.2rem;
  }
}
</style>
