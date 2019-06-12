<template>
  <v-layout>
    <v-flex xs12 sm6 offset-sm3>
      <v-card>
        <v-img
          v-bind:src="avatar"
        ></v-img>
        <v-card-title primary-title>
          <div>
            <h3 class="headline mb-0">{{name}}</h3>
            <ul>
              <li>Company: {{company}}</li>
              <li>Followers: {{followers}}</li>
              <li>Following: {{following}}</li>
              <li>Repos: {{repos}}</li>
            </ul>
          </div>
        </v-card-title>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  name: 'UserCard',
  data: function () {
    return {
      name,
      company: '',
      avatar: '',
      followers: null,
      following: null,
      repos: null,
    }
  },
  props: {
    activeUser: {
      type: Object,
      required: false,
      default: () => ([]),
    },
  },
  watch: {
    activeUser: {
      handler(value, oldValue) {
        this.name = value.name
        this.company = value.company
        this.avatar = value.avatar_url
        this.followers = value.followers
        this.following = value.following
        this.repos = value.public_repos
      }
    }
  }
};
</script>

<style scoped>
ul {
  list-style: none;
}
</style>
