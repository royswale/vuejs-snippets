<template>
  <div class="list">
    <div class="items" v-if="!loading">
      <UserCard
        v-for="(user, index) in users"
        :key="index"
        v-bind:name="user.name"
        v-bind:email="user.email"
      />
    </div>
    <div v-if="loading" class="timeline-item">
      <SkeletonScreen v-for="(load, index) in loads" :key="index"/>
    </div>
  </div>
</template>

<script>

// 认识Skeleton Screen【屏幕加载骨架】
// https://juejin.im/post/59ef52226fb9a0451543135f

import UserCard from '@/components/UserCard'
import SkeletonScreen from '@/components/SkeletonScreen'

export default {
  name: 'List',
  data () {
    return {
      users: [],
      loading: true,
      loads: 10
    }
  },
  components: {
    UserCard,
    SkeletonScreen
  },
  methods: {
    getUsers () {
      fetch('https://jsonplaceholder.typicode.com/users')
        .then(result => result.json())
        .then(result => {
          this.users = result
          this.loading = false
        })
    }
  },
  created () {
    setTimeout(() => {
      this.getUsers()
    }, 1000)
  }
}
</script>

<style lang="scss" scoped>
// .timeline-item {
.list {
  background: #fff;
  border: 1px solid;
  border-color: #e5e6e9 #dfe0e4 #d0d1d5;
  border-radius: 3px;
  padding: 12px;
  margin: 0 auto;
  max-width: 472px;
  min-height: 200px;
}
</style>
