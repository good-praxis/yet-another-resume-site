<template>
  <section class="masthead" role="img" aria-label="Image Description">
    <transition name="fade" mode="out-in">
      <h1>
        I'm a
        <transition
          name="fade"
          v-on:after-enter="fadeDelay"
          v-on:after-leave="updateTerm"
        >
          <span v-if="show" id="dynamicText">{{ term }}</span>
        </transition>
      </h1>
    </transition>
  </section>
</template>

<script>
export default {
  name: "Hero",
  data() {
    return {
      terms: [
        "Software Engineer",
        "Contributer",
        "Web Developer",
        "Programmer",
        "Technomancer",
        "Cat Person",
        "Fan of Open Source Software",
        "Server Whisperer",
        "Coder"
      ],
      show: false
    };
  },
  computed: {
    term() {
      return this.terms[0];
    }
  },
  methods: {
    updateTerm() {
      let temp = this.terms.shift();
      this.terms.push(temp);
      this.show = true;
    },
    fadeDelay() {
      setTimeout(() => {
        this.show = !this.show;
      }, 5000);
    }
  },
  created() {
    setTimeout(() => {
      this.show = !this.show;
    }, 1000);
  }
};
</script>

<style scoped>
.masthead {
  display: flex;
  justify-content: top;
  align-items: left;
  flex-direction: column;
  text-align: left;
  width: 100%;
  height: 80vh; /* if you don't want it to take up the full screen, reduce this number */
  overflow: hidden;
  background-size: cover !important;
  background: linear-gradient(
      to top,
      rgba(0, 0, 0, 0) 0%,
      rgba(0, 0, 0, 0) 37%,
      rgba(0, 0, 0, 0.65) 100%
    ),
    url(/berlin.jpeg) no-repeat center center scroll;
}

h1 {
  font-style: normal;
  font-weight: bold;
  color: #eee;
  font-size: 11vmin;
  letter-spacing: 0.03em;
  line-height: 1;
  text-shadow: 1px 2px 4px rgba(0, 0, 0, 0.8);
  margin-bottom: 40px;
  margin-top: 20vh;
  margin-left: 2%;
}

.fade-enter-active {
  transition: opacity 0.8s ease-in;
}
.fade-leave-active {
  transition: opacity 0.8s ease-out;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

@media screen and (min-device-width: 375px) and (max-device-width: 812px) {
  .masthead {
    text-align: center;
    align-items: center;
  }

  h1 {
    margin-left: 0;
    margin-top: 40vh;
  }
  span {
    display: block;
  }
}
</style>
