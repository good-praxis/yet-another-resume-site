<template>
  <v-timeline :dense="mobile">
    <v-timeline-item v-for="(employer, i) in history" :key="i" small>
      <template v-if="!mobile" v-slot:opposite>
        <h2 class="headline font-weight-bold">{{ employer.employer }}</h2>
        <p class="text-overline">
          <v-btn
            v-if="i % 2 == 0"
            depressed
            plain
            :href="employer.companyProfile"
            >{{ mobile }}<v-icon>mdi-linkedin</v-icon></v-btn
          >
          {{ employer.location }}
          <v-btn
            v-if="mobile || i % 2 != 0"
            depressed
            plain
            :href="employer.companyProfile"
            ><v-icon>mdi-linkedin</v-icon></v-btn
          >
        </p>
        <v-btn depressed plain @click="employer.expand = !employer.expand"
          >See {{ employer.expand ? "Less &uarr;" : "More &darr;" }}</v-btn
        >
        <v-expand-transition>
          <p v-show="employer.expand">{{ employer.companyBlurb }}</p>
        </v-expand-transition>
      </template>
      <div v-if="mobile">
        <h2 class="headline font-weight-bold">{{ employer.employer }}</h2>
        <p class="text-overline">
          <v-btn
            v-if="!mobile && i % 2 == 0"
            depressed
            plain
            :href="employer.companyProfile"
            ><v-icon>mdi-linkedin</v-icon></v-btn
          >
          {{ employer.location }}
          <v-btn
            v-if="mobile || i % 2 != 0"
            depressed
            plain
            :href="employer.companyProfile"
            ><v-icon>mdi-linkedin</v-icon></v-btn
          >
        </p>
        <v-btn depressed plain @click="employer.expand = !employer.expand"
          >See {{ employer.expand ? "Less &uarr;" : "More &darr;" }}</v-btn
        >
        <v-expand-transition>
          <p v-show="employer.expand">{{ employer.companyBlurb }}</p>
        </v-expand-transition>
      </div>
      <div
        v-for="(employment, j) in employer.employments"
        :key="j"
        class="py-4"
      >
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
          <li v-for="(task, k) in employment.taskBlurbs" :key="k">
            {{ task }}
          </li>
        </ul>
      </div>
    </v-timeline-item>
  </v-timeline>
</template>

<script>
export default {
  data() {
    return {
      mobile: false,
      history: [
        {
          expand: false,
          employer: "Avacon AG",
          employments: [
            {
              startDate: new Date(2016, 4),
              endDate: new Date(2017, 7),
              jobTitle: "Intern (various departments)",
              taskBlurbs: [
                "Performed server maintenance, repaired hardware defects in the energy observatory, installed new systems and services.",
                "Performed multi-level system monitoring, user administration, maintained on-premise hypervisors.",
                "Replaced an unstructured internal support request workflow with an ISO 27001-compliant digital workflow.",
                "Planned, prepared and monitored a penetration test of our critical infrastructure (KRITIS).",
                "Conceptualized, built and maintained the internal documentation system 'IS@Grid'."
              ],
              attachment: {
                link: "DarianReck_LetterOfRecommendations_Avacon_GER.pdf",
                title: "Letter Of Recommendations (German)"
              }
            }
          ],
          location: "Salzgitter, Germany",
          companyProfile: "https://www.linkedin.com/company/avaconag/",
          companyBlurb: `As one of the largest regional energy service providers in Germany, Avacon brings energy exactly where millions of people need it. Fast, reliable, efficient and environmentally friendly. They are your partner for regional energy solutions in the areas of electricity, gas, water, heating, cooling, telecommunications, mobility and lighting. Through their intelligent energy networks, they connect people from the North Sea coast to southern Hesse, in Lower Saxony and Saxony-Anhalt. 
                        \nWith around 2,100 employees and about 190 trainees, the Avacon group of companies is one of the largest employers and trainers in the region. `
        },
        {
          expand: false,
          employer: "Factory Works GmbH",
          employments: [
            {
              startDate: new Date(2018, 1),
              endDate: new Date(2019, 2),
              jobTitle: "Working Student Software Engineer",
              taskBlurbs: [
                "Initially focused on back-end work, rapidly learning Elixir and developing production code within the first two months of employment.",
                "Worked with a hybrid process consisting of Kanban and Scrum.",
                "Added missing documentation and conducted frequent code reviews with colleagues.",
                "Eventually my contribution shifted to full-stack work (React, Elixir) as I adapted to the company's needs.",
                "Utilized styled components along with style guides to ensure code quality.",
                "Designed APIs with external partners, actively working with freelancers towards the end of my tenure."
              ]
            }
          ],
          location: "Berlin, Germany",
          companyProfile: "https://www.linkedin.com/company/factory-berlin/",
          companyBlurb: `Factory Berlin is a membership organisation that offers a variety of products and programs for individuals, startups, and corporates in tech, digital innovation and entrepreneurship. In exchange for a monthly fee, members have access to workspace in two locations in Berlin, 400 social and educational events a year, entrepreneurship and creative mentorship programs, and online and offline networking activities. Factory Berlin creates partnerships with global organisations like Google and McKinsey, giving startups access to resources that help their businesses grow. Factory Berlin also offers event management services.`
        },
        {
          expand: false,
          employer: "CODE Education GmbH",
          employments: [
            {
              startDate: new Date(2018, 5),
              endDate: new Date(2019, 4),
              jobTitle: "Team Coach",
              taskBlurbs: [
                "Consulted with teams to work out interpersonal issues that hold back progress.",
                "Applying coaching frameworks, including the GROW model.",
                "Provided coaching on interpersonal topics, such as microaggressions and methods to increase commitment."
              ]
            },
            {
              startDate: new Date(2019, 3),
              endDate: new Date(2019, 11),
              jobTitle: "Software Engineer",
              taskBlurbs: [
                "Maintained our Elixir digital learning platform until it was phased out.",
                "Conceptualized and built a new digital learning platform on a TypeScript, React and Prisma (GraphQL) stack.",
                "Implementation of full feature suites for our learning platform, e.g. allowing the authorized recording of assessments.",
                "Onboarded student workers into our processes and codebase, offering consultation for development and process optimization.",
                "Worked within an Agile team, dealing with fast changing requirements of stakeholders.",
                "Quick iteration on features thanks to the application of the Ant Design design system."
              ],
              attachment: {
                link: "DarianReck_LetterOfRecommendations_CODE_GER.pdf",
                title: "Letter Of Recommendations (German)"
              }
            }
          ],
          location: "Berlin, Germany",
          companyProfile: "https://www.linkedin.com/school/codeuniversity/",
          companyBlurb: `CODE Education GmbH is the legal company behind the CODE University of Applied Science. CODE University of Applied Sciences is a private, state-recognized University of Applied Sciences for digital product development in Berlin.`
        }
      ]
    };
  },
  methods: {
    formatDate(date) {
      let formatter = new Intl.DateTimeFormat("en-US", {
        month: "long",
        year: "numeric"
      });
      return formatter.format(date);
    }
  },
  created() {
    if (process.client)
      this.windowMobilePoller = setInterval(() => {
        this.mobile = window.innerWidth < 700;
      });
  },
  beforeDestroy() {
    return clearInterval(this.windowMobilePoller);
  }
};
</script>

<style lang="scss" scoped></style>
