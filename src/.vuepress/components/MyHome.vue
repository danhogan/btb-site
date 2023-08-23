<template>
  <div class="home">
    <link href="https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet" integrity="sha384-wvfXpqpZZVQGK6TAh5PVlGOfQNHSoD2xbE+QkPxCAFlNEevoEH3Sl0sibVcOQVnN" crossorigin="anonymous">
    <link href="https://fonts.googleapis.com/css2?family=Caveat&family=Karla&display=swap" rel="stylesheet">
    <div class="heroContainer">
      <h1>Dan Hogan</h1>
        <h2>Professional Steward of Various Beeps and Boops</h2>
    </div>
    <div class="links">
        <div>
            <a href="#projects">
                <i class="fa fa-image"></i>
                <span>Projects</span>
            </a>
        </div>
        <div>
            <a target="_blank" href="https://github.com/danhogan">
                <i class="fa fa-github"></i>
                <span>Github</span>
            </a>
        </div>
        <div>
            <a target="_blank" href="https://www.linkedin.com/in/iamdanhogan/">
                <i class="fa fa-linkedin"></i>
                <span>LinkedIn</span>
            </a>
        </div>
        <div>
            <a target="_blank" href="https://twitter.com/BelowTheBenthic">
                <i class="fa fa-twitter"></i>
                <span>Twitter</span>
            </a>
        </div>
        <div>
            <a href="/blog">
                <i class="fa fa-pencil"></i>
                <span>Blog</span>
            </a>
        </div>
    </div>

    <h2 id="projects">Projects</h2>
    <div class="projectsContainer">
        <div class="project" v-for="project in projects">
            <h3>{{project.title}}</h3>
            <div class="tech">
                <div v-for="tech in project.tech">{{tech}}</div>
            </div>
            <p>{{project.description}}</p>
            <div class="links">
                <a v-if="project.link" :href="project.link" target="_blank">Project</a>
                <a v-if="project.github" :href="project.github" target="_blank">Github</a>
            </div>
        </div>
    </div>

    <!-- https://maximpekarsky.com/-->

    <!-- <style>
            body {
                background: linear-gradient(41deg, rgba(107, 107, 107, 0.04) 0%, rgba(107, 107, 107, 0.04) 8%,rgba(31, 31, 31, 0.04) 8%, rgba(31, 31, 31, 0.04) 100%),linear-gradient(9deg, rgba(228, 228, 228, 0.04) 0%, rgba(228, 228, 228, 0.04) 62%,rgba(54, 54, 54, 0.04) 62%, rgba(54, 54, 54, 0.04) 100%),linear-gradient(124deg, rgba(18, 18, 18, 0.04) 0%, rgba(18, 18, 18, 0.04) 37%,rgba(233, 233, 233, 0.04) 37%, rgba(233, 233, 233, 0.04) 100%),linear-gradient(253deg, rgba(201, 201, 201, 0.04) 0%, rgba(201, 201, 201, 0.04) 55%,rgba(47, 47, 47, 0.04) 55%, rgba(47, 47, 47, 0.04) 100%),linear-gradient(270deg, rgba(172, 172, 172, 0.04) 0%, rgba(172, 172, 172, 0.04) 33%,rgba(26, 26, 26, 0.04) 33%, rgba(26, 26, 26, 0.04) 100%),linear-gradient(64deg, rgba(11, 11, 11, 0.04) 0%, rgba(11, 11, 11, 0.04) 38%,rgba(87, 87, 87, 0.04) 38%, rgba(87, 87, 87, 0.04) 100%),linear-gradient(347deg, rgba(199, 199, 199, 0.04) 0%, rgba(199, 199, 199, 0.04) 69%,rgba(4, 4, 4, 0.04) 69%, rgba(4, 4, 4, 0.04) 100%),linear-gradient(313deg, rgba(36, 36, 36, 0.04) 0%, rgba(36, 36, 36, 0.04) 20%,rgba(91, 91, 91, 0.04) 20%, rgba(91, 91, 91, 0.04) 100%),linear-gradient(90deg, rgb(10, 17, 72),rgb(35, 148, 228));
                background-repeat: no-repeat;
                background-attachment: fixed;
            }
    </style>-->
  </div>
</template>

<script>
export default {
    data() {
        return {
            projects: [
                {
                    title: "Sultans of Stats Website",
                    tech: ["Next.js", "React", "TypeScript", "ApexCharts"],
                    description: "Fantasy baseball site with aggregate roto leaderboard for Sultans of Stats league of leagues (298 teams).",
                    link: "https://www.sultansofstats.com/",
                    github: "https://github.com/danhogan/sultansofstats",
                    img: ""
                },
                {
                    title: "TopesCalc",
                    tech: ["Vue.js", "TypeScript", "Vuetify"],
                    description: "A battle calculator for the game Polytopia.",
                    link: "https://topescalc.netlify.app/",
                    github: "https://github.com/danhogan/topescalc",
                    img: ""
                },
                {
                    title: "Batted Ball Data",
                    tech: ["Vue.js", "Vuetify", "ApexCharts", "Python"],
                    description: "A look at baseball batted ball data.",
                    link: "https://danhogan.github.io/batted-ball/",
                    github: "https://github.com/danhogan/batted-ball",
                    img: ""
                },
                {
                    title: "Fantasy Baseball Charts",
                    tech: ["JavaScript", "Node.js", "Express", "Cheerio", "D3.js"],
                    description: "A project that scrapes a fantasy baseball league on ESPN and displays weekly totals over the course of a season.",
                    link: "http://danhogan.github.io/fantasy-baseball-charts/",
                    github: "https://github.com/danhogan/fantasy-baseball-scrape",
                    img: ""
                },
                {
                    title: "This Site",
                    tech: ["Vuepress", "Vue.js", "JavaScript"],
                    description: "My personal site and blog.",
                    link: "http://belowthebenthic.com/",
                    github: "https://github.com/danhogan/btb-site",
                    img: ""
                },
                {
                    title: "UDL Site",
                    tech: ["Vuepress", "Vue.js", "JavaScript"],
                    description: "A website for my fantasy baseball league: Ultimate Dynasty League.",
                    link: "https://udl.netlify.app/",
                    github: "https://github.com/danhogan/udl-site",
                    img: ""
                },
                {
                    title: "Misplaced Hashtags",
                    tech: ["Node.js", "Twitter API"],
                    description: "A goofy Twitter bot that swaps around trending hashtags.",
                    link: "https://twitter.com/misplacedtags",
                    github: "",
                    img: ""
                },
                {
                    title: "Cheesy Tweets",
                    tech: ["Node.js", "Express", "Socket.io", "WebGL/Three.js", "Twitter API"],
                    description: "If you want to look at what everyone says about cheese on Twitter while viewing a pulsing cube that was eventually going to look like a wedge of cheese, you've come to the right place. Also, find help.",
                    link: "",
                    github: "https://github.com/danhogan/CheesyTweets",
                    img: ""
                },
                {
                    title: "NFL Tweets",
                    tech: ["Node.js", "Express", "Socket.io", "Twitter API"],
                    description: "Displays side-by-side streams and counters on two keywords in a Twitter search. I made it Bears vs Packers.",
                    link: "",
                    github: "https://github.com/danhogan/NFLTweets",
                    img: ""
                },
                {
                    title: "Twitter Stream Data",
                    tech: ["Node.js", "Express", "Socket.io", "D3.js", "Twitter API"],
                    description: "A beginning look at a specific search term on Twitter. Tracks tweets/minute and displays bar graphs.",
                    link: "",
                    github: "https://github.com/danhogan/TwitterStreamData",
                    img: ""
                }
            ]
        };
    }
}
</script>

<style>
body {
    background-color: #281552;
    color: #ccc;
    font-family: 'Karla', sans-serif;
}

html {
    scroll-behavior: smooth;
}
</style>

<style scoped>
h1,
h2 {
  text-align: center;
}

h1 {
  font-size: 5em;
  margin-bottom: 0;
  font-family: 'Caveat', cursive;
}

h2 {
    font-size: 2em;
    margin-block-start: 0.83em;
    margin-block-end: 0.83em;
}

.heroContainer {
  margin-top: 10em;
}

.links {
    margin-top: 4em;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
    text-align: center;
}

/* https://codepen.io/davidicus/pen/emgQKJ */
* {
  box-sizing: inherit;
  transition-property: all;
  transition-duration: .6s;
  transition-timing-function: ease;
}

.links > div {
    letter-spacing: 0;
    cursor: pointer;
    font-size:16px;
    font-weight: 400;
    line-height: 45px;
    margin: 0 0 2em;
    max-width: 160px; 
    position: relative;
    text-decoration: none;
    width: 100%; 
}

.links > div:hover,
.links > div:active {
    letter-spacing: 5px;
}

.links > div:after,
.links > div:before {
    backface-visibility: hidden;
    border: 1px solid #281552;
    bottom: 0px;
    content: " ";
    display: block;
    margin: 0 auto;
    position: relative;
    /* transition: all 280ms ease-in-out; */
    width: 0;
}

.links > div:hover:after,
.links > div:hover:before {
    backface-visibility: hidden;
    border-color: #CCC;
    transition: width 350ms ease-in-out;
    width: 70%;
}

.links > div:hover:before {
    bottom: auto;
    top: 0;
    width: 70%;
}

.links a {
    text-decoration: none;
    color: #ccc;
}

.links i {
    display: block;
    font-size: 2em;
    margin-bottom: 0.2em;
}

#projects {
    margin-top: 7em;
}

.projectsContainer {
    display: grid;
    grid-template-columns: 1fr 1fr;
    column-gap: 1em;
}

.project {
    background-color: #3C1F7B;
    border-radius: 5px;
    box-shadow: 0px 5px 4px #160b2e;
    padding: 1em;
    margin-bottom: 2em;
}

.tech > div {
    background-color: #281552;
    color: #CCC;
    margin: 0.5em 1em;
    border-radius: 10px;
    padding: 0.5em;
    display: inline-block;
}

.tech {
    margin-left: -1em;
}
</style>