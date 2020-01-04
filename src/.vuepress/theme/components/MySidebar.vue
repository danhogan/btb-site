<template>
    <div class="mySidebar">
        <div class="leagueLeaders">
            <h4>League Leaders - End of June</h4>
            <div class="leaderCategory" v-for="cat in categories">
                <div class="topPart">
                    <div>{{cat.category}} - {{cat.value}} - {{cat.udlTeam}}</div>
                    <!-- <img :src="cat.udlTeamLogo"> -->
                </div>
                <img class="playerImage" :src="cat.playerImage">
                <div class="majorContributor">Major Contributor - {{cat.playerName}}</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["categories"],
    data() {
        return {
            
        };
    }
};
</script>

<style scoped>
    .mySidebar {
        margin-top: 3.6rem;
        /* width: 15em; */
        width: 15%;
    }

    @media only screen and (max-width: 600px) {
        .mySidebar {
            width: 100%;
        }
    }

    .playerImage {
        max-width: 100%;
    }

    .leaderCategory {
        border-bottom: 1px solid #EEE;
        padding-bottom: .5em;
        margin-bottom: .5em;
    }

    .topPart {
        margin-bottom: .3em;
    }

    .majorContributor {
        font-size: 0.9em;
    }
</style>