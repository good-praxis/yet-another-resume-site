<template>
  <v-card id="contact-form">
    <v-form ref="form" v-model="valid" lazy-validation>
      <v-container>
        <v-card-title class="headline">
          Contact Form
        </v-card-title>
        <v-card-text>
          <v-row>
            <v-col cols="12" md="6">
              <v-text-field
                v-model="name"
                :rules="nameRules"
                label="Name"
                required
              >
              </v-text-field>
            </v-col>
            <v-col cols="12" md="6">
              <v-text-field
                v-model="email"
                :rules="emailRules"
                label="E-mail"
                required
              >
              </v-text-field>
            </v-col>
          </v-row>

          <v-textarea
            v-model="message"
            :rules="messageRules"
            label="Message"
            required
          >
          </v-textarea>
        </v-card-text>
      </v-container>

      <v-card-actions>
        <v-spacer />
        <v-btn :disabled="!valid" color="success" class="mr-4" @click="submit">
          Send
        </v-btn>

        <v-snackbar v-model="snackbar">
          {{ snackbarText }}

          <template v-slot:action="{ attrs }">
            <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
              Close
            </v-btn>
          </template>
        </v-snackbar>

        <v-btn color="error" class="mr-4" @click="reset">
          Clear
        </v-btn>
      </v-card-actions>
      <hr />
      <v-card-subtitle>
        <v-btn depressed plain href="https://www.emailjs.com/"
          >Powered by EmailJS</v-btn
        >
        |
        <v-btn
          depressed
          plain
          href="https://www.emailjs.com/legal/terms-of-service/"
          >Terms Of Service</v-btn
        >
        -
        <v-btn
          depressed
          plain
          href="https://www.emailjs.com/legal/privacy-policy/"
          >Privacy Policy</v-btn
        ></v-card-subtitle
      >
    </v-form>
  </v-card>
</template>

<script>
import { init, send } from "emailjs-com";
init("user_BpVCX7oYjWgrOoyvkkl4v");

export default {
  data() {
    return {
      valid: true,
      snackbar: false,
      snackbarText: "",
      name: "",
      nameRules: [
        v => !!v || "Name is required",
        v => (v && v.length <= 30) || "Name must be less than 30 characters"
      ],
      email: "",
      emailRules: [
        v => !!v || "E-mail is required",
        v => /.+@.+\..+/.test(v) || "E-mail must be valid"
      ],
      message: "",
      messageRules: [v => !!v || "Message is required"]
    };
  },
  methods: {
    submit() {
      this.$refs.form.validate();
      if (this.valid) {
        this.valid = false;
        send("service_mwrzr8p", "template_vdmdg6f", {
          reply_to: this.email,
          message: this.message,
          from_name: this.name
        }).then(
          result => {
            this.snackbar = true;
            this.snackbarText = "Message successfully sent!";
            this.reset();
          },
          error => {
            this.valid = true;
            this.snackbarText =
              "Some error occured with EmailJS, either try again or reach out to me at darian.reck@pm.me!";
            this.snackbar = true;
          }
        );
      }
    },
    reset() {
      this.$refs.form.reset();
    }
  }
};
</script>

<style scoped></style>
