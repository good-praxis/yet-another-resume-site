<template>
  <v-app dark>
    <v-main>
      <hero />
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer
      :absolute="!fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
import Hero from '@/components/Hero.vue';

export default {
  components: {
    Hero
  },
  data () {
    return {
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
      ],
      title: 'Vuetify.js'
    }
  }
}
</script>
