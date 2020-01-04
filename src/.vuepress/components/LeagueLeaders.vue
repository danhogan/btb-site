<template>
    <div class="leadersContainer">
        <div class="leagueLeaders" v-for="i in 2">
            <div class="leaderCategory" v-for="cat in categories.slice(i*5-5, i*5)">
                <div class="topPart">
                    <div class="catTitle">
                        <h5>{{cat.category}} - {{cat.value}}</h5>
                        <h5>{{cat.udlTeam}}</h5>
                    </div>
                    <div class="teamImageContainer">
                        <img :src="cat.udlTeamLogo">
                    </div>
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
    .leadersContainer {
        display: grid;
        grid-template-columns: auto auto;
        grid-column-gap: 1em;
    }

    .leagueLeaders {
        display: grid;
        grid-template-columns: auto;
        grid-row-gap: 1em;
    }

    @media only screen and (max-width: 1024px) {
        .leadersContainer {
            grid-template-columns: auto;
            grid-row-gap: 1em;
        }
    }

    .playerImage {
        display: block;
        width: 100%;
        height: 15em;
        object-fit: cover;
    }

    .leaderCategory {
        border-bottom: 1px solid #EEE;
        margin-bottom: .5em;
        box-shadow: 0 4px 6px 0 hsla(0, 0%, 0%, 0.2);
    }

    .topPart {
        display: grid;
        grid-template-columns: 65% 35%;
    }

    .teamImageContainer {
        width: 100%;
        height: 5em;
        object-fit: cover;
    }

    .majorContributor {
        font-size: 0.9em;
        text-align: center;
        padding: .3em;
    }

    .catTitle {
        font-size: 1.4em;
        margin: auto;
    }

    .catTitle > h5 {
        margin: 0;
    }
</style>