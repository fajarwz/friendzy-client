<template>
  <div class="bg-green-500 text-white text-md">
    <nav class="container flex justify-between items-center mx-auto py-5">
      <span class="font-semibold text-2xl"> Friendzy </span>
      <div class="space-x-2">
        <template v-if="isLoggedIn">
          <span>Welcome,
            <nuxt-link to="#" class="hover:text-green-200">{{ name }}</nuxt-link>
          </span>
          <nuxt-link to="/friends" class="hover:text-green-200">Friends</nuxt-link>
          <nuxt-link to="/users" class="hover:text-green-200">Users</nuxt-link>
          <nuxt-link to="/dashboard" class="hover:text-green-200">Dashboard</nuxt-link>
          <button @click="logout" class="hover:text-green-200">Logout</button>
        </template>
        <template v-else>
          <nuxt-link to="/auth/register" class="hover:text-green-200">Register</nuxt-link>
          <nuxt-link to="/auth/login" class="hover:text-green-200">Login</nuxt-link>
        </template>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  computed: {
    isLoggedIn: function() {
      return this.$auth.loggedIn
    },

    name: function() {
      return this.$auth.user.name
    }
  },
  methods: {
    logout() {
      this.$auth.logout();
    },
  },
};
</script>