<template>
    <v-timeline>
        <pre>{{history}}</pre>
    </v-timeline>
</template>

<script>
    export default {
        data() {
            return {
                history: [
                    {
                        employer: "Avacon AG",
                        startDate: new Date(2016, 4),
                        endDate: new Date(2017, 7),
                        location: "Salzgitter",
                        companyProfile: "https://www.linkedin.com/company/avaconag/",
                        attachment: "DarianReck_LetterOfRecommendations_Avacon_GER.pdf"                           
                    },
                    {},
                    {},
                    {}
                ]
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>