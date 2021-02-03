<template>
  <v-app dark>
    <v-main>
      <hero />
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer :absolute="!fixed" app>
      <v-spacer />
      <span>
        &copy; {{ new Date().getFullYear() }} Darian Reck - Made with ❤️ + ☕ +
        Vue - Look at the
        <v-btn
          depressed
          plain
          id="github-btn"
          href="https://github.com/good-praxis/yet-another-resume-site"
          >Source Code</v-btn
        >
      </span>
    </v-footer>
  </v-app>
</template>

<script>
import Hero from "@/components/Hero.vue";

export default {
  components: {
    Hero
  },
  data() {
    return {
      fixed: false,
      items: [
        {
          icon: "mdi-apps",
          title: "Welcome",
          to: "/"
        }
      ],
      title: "Vuetify.js"
    };
  }
};
</script>

<style>
#github-btn {
  padding-left: 0;
  padding-right: 4px;
}
</style>
