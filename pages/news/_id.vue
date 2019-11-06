<template>
  <div v-html="content"></div>
</template>

<script>
export default {
  data () {
    return {
      content: '2211'
    }
  },
  async asyncData (ctx) {
    let id = ctx.params.id
    const result = await ctx.$axios.$get('https://cnodejs.org/api/v1/topic/' + id)
    const content = result.data.content
    return { content }
  },
}
</script>