<template>
    <v-card elevation="24">
        <v-card-title class="headline">
          Versatile Software Devel&shy;oper based in Berlin
        </v-card-title>
        <v-card-text>
          <span v-html="blurb" />
        </v-card-text>
        <v-card-actions>
          <div class="text-xs-right signature">
            <em><small>&mdash; <v-avatar size="62"><img src="avatar.jpg" alt="Darian"></v-avatar>
 Darian Reck</small></em>
          </div>
          <v-spacer />
          <v-btn
            color="primary"
            @click="scrollToForm"
          >
            Contact Me
            <v-icon class="icon">mdi-send</v-icon>
          </v-btn>
        </v-card-actions>
      </v-card>
</template>

<script>
    
    export default {
        data() {
            return {
              blurb: "<span>I'm an autodidact, immersing myself in the Web Development Space for over 3 years. I've worked with both start-ups and large enterprises. Skilled in <b>Rust</b>, <b>React</b> and <b>Vue</b>. Always interested in new technologies \& frameworks. Worked with a focus on <b>Elixir</b> for 1+ year. Runs <b>Manjaro</b> and <b>MacOS</b>. Experienced in <b>DevOps</b> activities, including <b>Docker</b>, and I've deployed and set up <b>remote root servers</b> and local hardware, as well as <b>vServers</b>, according to the needs of the project or product. Enthusiastic about game making and <b>interactive storytelling</b>. Believes in free software.</span>",
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
    .headline {
      hyphens: manual;
      word-break: keep-all;
    }
    .v-icon {
      margin-left: 10px;
      margin-top: -2px
    }

    .signature {
      color: rgba(255, 255, 255, .6)
    }
</style>