<template>
  <div>
    <h1>This is fun page!</h1>
    <NuxtLogo />
    <div @click="onClickHome">Home page</div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  asyncData(context) {
    console.log('asyncData context', context);
  },
  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start()
      setTimeout(() => this.$nuxt.$loading.finish(), 500)
    })
  },
  async fetch() {
    const posts = await this.$http.$get('https://api.nuxtjs.dev/posts')
    console.log('posts', posts);
  },
  methods: {
    onClickHome() {
      this.$router.push("/");
    }
  }
})
</script>
