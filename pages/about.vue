<template>
    <main>
      <div v-if="!this.$fetchState.pending">
        About Page rendered on <h3>{{rendering}}</h3>
        {{test}}

        <button @click="test='clicked';$fetch()">click to refresh</button>
      </div>
      <div v-else>
        Please wait while we fetch your data
      </div>
    </main>
  </template>
  
  <script>
  export default {
    head() {
      return {
        title: 'about',
        meta: [
          {
            hid: 'about',
            name: 'about',
            content: 'Home about description'
          }
        ]
      }
    },
    name: 'AboutPage',
    layout: 'blog',
    data () {
        return {
            test: 'hello'
        }
    },
    async fetch() {
      console.log('hello')
      this.test = await new Promise((resolve) => setInterval(() => { resolve('api response') }, 5000))
    },
    fetchOnServer: false,
    async asyncData(context) {
      //  console.log('hello-asyncdata')
      //  console.log(await new Promise((resolve) => setInterval(() => { resolve('api response') }, 5000)))
      return {
        rendering: process.server ? 'server' : 'client'
      }
    },
    mounted () {
       console.log("Im mounted")
    }
  }
  </script>