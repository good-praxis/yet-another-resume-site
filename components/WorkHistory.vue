<template>
  <v-timeline :dense="mobile">
    <v-timeline-item v-for="(employer, i) in history" :key="i" small>
      <template v-if="!mobile" v-slot:opposite>
        <CompanyInfo :left="i % 2 == 0" :company="employer" />
      </template>
      <span v-if="mobile">
        <CompanyInfo :company="employer" />
      </span>
      <Employments :employmentsData="employer.employments" />
    </v-timeline-item>
  </v-timeline>
</template>

<script>
import CompanyInfo from "@/components/CompanyInfo.vue";
import Employments from "@/components/Employments.vue";

export default {
  components: { CompanyInfo, Employments },
  data() {
    return {
      mobile: false,
      historyData: [
        {
          companyName: "Avacon AG",
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
          companyName: "Factory Works GmbH",
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
          companyName: "CODE Education GmbH",
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
        },
        {
          companyName: "Freelance & Tech Volunteering",
          employments: [
            {
              startDate: new Date(2020, 2),
              current: true,
              jobTitle: "Tech Worker",
              taskBlurbs: [
                "Due to the pandemic I started to tech volunteering for NGOs within my network, as well as general freelancing",
                "From server setup, through developing UI components, to writing usability userscripts.",
                "Some of the technologies I used during this time are Ansible, Nginx, Nuxt, Drupal, MutationObserver API, Emotion, Vuex, Ramda."
              ]
            }
          ],
          location: "Berlin, Germany",
        }
      ]
    };
  },
  computed: {
    history() {
      this.historyData.reverse();
      return this.historyData;
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
