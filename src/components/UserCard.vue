<template>
  <div>
    <div>
      {{company}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'UserCard',
  data: function () {
    return {
      company: ''
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
        this.company = value.company
      }
    }
    }
};
</script>
