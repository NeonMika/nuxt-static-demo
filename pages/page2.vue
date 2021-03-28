<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">nuxt-static-demo</h1>
      <div class="links">
        <nuxt-link to="/" class="button--green"> Index </nuxt-link>
      </div>

      <div></div>
      <div>
        {{ fetchTime }}
      </div>
      <div>
        {{ asyncTime }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      fetchTime: 'loading',
    }
  },
  fetch: async function () {
    console.log('fetch page2')
    this.fetchTime = await this.$axios.$get('http://worldtimeapi.org/api/ip')
  },
  asyncData: async function ({ $axios }) {
    console.log('asyncData page2')
    const asyncTime = await $axios.$get('http://worldtimeapi.org/api/ip')
    return { asyncTime }
  },
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
