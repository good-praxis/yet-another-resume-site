<template>
  <span>
    <div v-for="(employment, i) in employments" :key="i" class="py-4">
      <h2 class="headline font-weight-light mb-4">
        {{ employment.jobTitle }}
        <v-tooltip right v-if="employment.attachment">
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              v-on="on"
              v-bind="attrs"
              :href="employment.attachment.link"
              target="_blank"
              depressed
              plain
            >
              <v-icon>mdi-download</v-icon>
            </v-btn>
          </template>
          <span>{{ employment.attachment.title }}</span>
        </v-tooltip>
      </h2>
      <p class="text-subtitle-2">
        {{ formatDate(employment.startDate) }} -
        {{ formatDate(employment.endDate) }}
      </p>
      <ul>
        <li v-for="(task, j) in employment.taskBlurbs" :key="j">
          {{ task }}
        </li>
      </ul>
    </div>
  </span>
</template>

<script>
export default {
  props: {
    employments: {
      type:
        Array[
          {
            jobTitle: {
              type: String,
              default: "Code Monkey"
            },
            startDate: {
              type: Date
            },
            endDate: {
              type: Date
            },
            attachment: {
              link: {
                type: String
              },
              name: {
                type: String
              }
            }
          }
        ]
    }
  },
  methods: {
    formatDate(date) {
      let formatter = new Intl.DateTimeFormat("en-US", {
        month: "long",
        year: "numeric"
      });
      return formatter.format(date);
    }
  }
};
</script>

<style lang="scss" scoped></style>
