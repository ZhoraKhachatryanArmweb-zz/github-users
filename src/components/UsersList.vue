<template>
  <div>
    <div v-for="user in users" v-bind:key="user.id">
      <div @click="sendUserId(user.id)">
        {{user.name}}
        <img v-bind:src="user.avatar">
        {{user.reposUrl}}
      </div>
    </div>
  </div>
</template>

<script>
import store from "../store/index"
export default {
  name: 'UsersList',
  methods: {
    sendUserId: function (userId) {
      this.$emit('user', userId)
    },
  },
  props: {
    users: {
      type: Array,
      required: false,
      default: () => ([]),
    },
  },
};
</script>

<style scoped>
img {
  width:100px;
}
</style>
