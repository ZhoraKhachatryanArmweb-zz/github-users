<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Main msg="Welcome to Your Vue.js App"/>
    <search-input
      placeholder="Type a GitHub username"
      @text="handleSearchUser"
    />
    <users-list
      :users="users"
      @user="userId => getUser(userId)"
    />
    <user-card
      :activeUser = "activeUser"
    />
  </div>
</template>

<script>
import Main from './components/Main.vue'
import store from "./store/index"
import SearchInput from '@/components/SearchInput.vue'
import UsersList from '@/components/UsersList.vue'
import UserCard from '@/components/UserCard.vue'
import { mapState } from 'vuex'
export default {
  name: 'app',
  methods : {
    handleSearchUser(username) {
      this.$store.dispatch('SEARCH_USERS', username);
    },
    getUser(userId) {
      this.$store.dispatch('GET_USER_ID', userId)
    }
  },
  components: {
    Main,
    SearchInput,
    UsersList,
    UserCard
  },
  computed: mapState(['users', 'activeUser']),
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
