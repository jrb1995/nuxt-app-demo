<template>
  <div v-html="content"></div>
</template>

<script>
export default {
  data () {
    return {
      title: '',
      content: '2211'
    }
  },
  head () {
    return {
      title: this.title
    }
  },
  async asyncData (ctx) {
    let id = ctx.params.id
    const result = await ctx.$axios.$get('https://cnodejs.org/api/v1/topic/' + id)
    const content = result.data.content
    const title = result.data.title
    return { content, title }
  },
}
</script>