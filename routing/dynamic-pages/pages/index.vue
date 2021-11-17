<template>
  <div>
    <ul v-for="mountain in mountains" :key="mountain.id">
        <li><a @click="call_m(mountain.continent.toLowerCase(),mountain.slug)">{{mountain.title}}</a></li>
    </ul>
    <ul v-for="mountain in mountains" :key="mountain.id">
      <NuxtLink :to="`${mountain.continent.toLowerCase()}/${mountain.slug}`">
        <li>{{ mountain.title }}</li>
      </NuxtLink>
    </ul>
  </div>
</template>
<script>
export default {
  async asyncData() {
    const mountains = await fetch(
      'https://api.nuxtjs.dev/mountains'
    ).then((res) => res.json())

    return { mountains }
  },
  methods: {
    call_m(m1, m2) {
      this.$router.push({ name: 'continent-mountain', params: { continent: m1, mountain: m2 } })
    }
  }
}
</script>
