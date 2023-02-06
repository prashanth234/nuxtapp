<template>
  <main>
    main page is rendered on {{rendering}}
    <NuxtLink to="/about" >Go to page about</NuxtLink>
  </main>
</template>

<script>
export default {
  name: 'IndexPage',
  head() {
      return {
        title: 'home',
        meta: [
          {
            hid: 'home',
            name: 'home',
            content: 'Home description'
          }
        ]
      }
    },
  asyncData() {
    return {
      rendering: process.server ? 'server' : 'client'
    }
  }
}
</script>
