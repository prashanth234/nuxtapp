<template>
    <main>hello</main>
</template>

<script>
export default {
    async asyncData(context) {
      console.log(process.server)
      const id = context.params.id
      try {
        // Using the nuxtjs/http module here exposed via context.app
        const post = await context.app.$http.$get(
          `https://api.nuxtjs.dev/posts/${id}`
        )
        return { post }
      } catch (e) {
        context.error(e) // Show the nuxt error page with the thrown error
      }
    },
    middleware({ store, redirect }) {
    // retrieving keys via object destructuring
        const isAuthenticated = true
        if (!isAuthenticated) {
        return redirect('/')
        }
    }
  }
</script>