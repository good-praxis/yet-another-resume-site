<template>
  <v-row justify="center" align="center">
    <v-col cols="14" sm="10" md="8">
      <profile />
      <work-history />
      <contact />
    </v-col>
  </v-row>
</template>

<script>
import Contact from "~/components/Contact.vue";
import Profile from "~/components/Profile.vue";
import WorkHistory from "~/components/WorkHistory.vue";

export default {
  components: { Profile, Contact, WorkHistory },
  layout: "cv",
};
</script>

<style>
#herotext {
  background-color: rgba(0, 0, 0, 0.5);
}
html {
  background-color: rgb(0, 0, 0);
  animation: fadein 2s;
}

@keyframes fadein {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
