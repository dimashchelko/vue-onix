<template lang="pug">
  ul
    li(v-for='link in links', :key='link')
      a(href='#')
        | {{ link }}
    li
      a.count(href='#')
        | Notifications
        span#counter {{elemInd}}
</template>

<script>
export default {
  props: [
    'index'
  ],
  data () {
    return {
      links: ['Home', 'My Tasks'],
      elemInd: 0
    }
  },
  mounted () {
    this.$root.$on('eventing', (index) => {
      this.elemInd = index
    })
  }
}
</script>
