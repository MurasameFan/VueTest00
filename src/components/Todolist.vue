<template>
  <li @click="handleClick">{{mycontent}}</li>
</template>

<script>
export default {
  name: 'Todolist',
  props: ['mycontent', 'index'],
  data () {
    return {}
  },
  methods: {
    handleClick () {
      this.$emit('delete', this.index)
    }
  }
}
</script>
