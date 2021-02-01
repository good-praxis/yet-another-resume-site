<template>
    <v-card id="contact-form">
        <v-card-title v-if="showFront" class="headline">
          Contact Form
        </v-card-title>
      </v-card>
</template>

<script>
    export default {
        data() {
            return {
                showFront: true
            }
        },
        methods: {
            scrollToForm() {
                const el = document.getElementById("contact-form")

                if(el) {
                  el.scrollIntoView({behavior: 'smooth'})
                }
            }
        }
    }
</script>

<style scoped>

</style>