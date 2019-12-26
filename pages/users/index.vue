<template>
  <section>
    <h1>Users Page</h1>
    <ul>
      <li v-for="user of users" :key="user.id">
        <a @click.prevent="openUser(user)" href="#">{{ user.name }}</a>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  // preloading data from backend
  async asyncData ({ $axios }) {
    const users = await $axios.$get('https://jsonplaceholder.typicode.com/users')
    return { users }
  },
  data () {
    return {
      users: []
    }
  },
  methods: {
    openUser (user) {
      this.$router.push('/users/' + user)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
