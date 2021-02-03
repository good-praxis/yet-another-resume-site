<template>
  <div class="company-info">
    <h2 class="headline font-weight-bold">{{ company.companyName }}</h2>
    <p class="text-overline">
      <v-btn v-if="left" depressed plain :href="company.companyProfile">
        <v-icon v-show="loaded">{{ linkedinIcon }}</v-icon>
      </v-btn>
      {{ company.location }}
      <v-btn v-if="!left" depressed plain :href="company.companyProfile"
        ><v-icon v-show="loaded">{{ linkedinIcon }}</v-icon></v-btn
      >
    </p>
    <v-btn depressed plain @click="expand = !expand"
      >See {{ expand ? "Less &uarr;" : "More &darr;" }}</v-btn
    >
    <v-expand-transition>
      <p v-show="expand">{{ company.companyBlurb }}</p>
    </v-expand-transition>
  </div>
</template>

<script>
import { mdiLinkedin } from "@mdi/js";
export default {
  data() {
    return {
      linkedinIcon: mdiLinkedin,
      expand: false,
      loaded: false
    };
  },
  props: {
    left: {
      type: Boolean
    },
    company: {
      companyName: {
        type: String,
        required: true
      },
      location: {
        type: String,
        required: true
      },
      companyProfile: {
        type: String
      },
      companyBlurb: {
        type: String,
        required: true
      }
    }
  },
  mounted() {
    this.loaded = true;
  }
};
</script>

<style lang="scss" scoped></style>
