<template>
  <div class="home">
    <link href="https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet" integrity="sha384-wvfXpqpZZVQGK6TAh5PVlGOfQNHSoD2xbE+QkPxCAFlNEevoEH3Sl0sibVcOQVnN" crossorigin="anonymous">
    <link href="https://fonts.googleapis.com/css2?family=Caveat&family=Karla&display=swap" rel="stylesheet">
    <div class="heroContainer">
      <h1>Dan Hogan</h1>
        <h2>Full-Stack Web Developer</h2>
    </div>
    <div class="links">
        <div>
            <i class="fa fa-user"></i>
            <span>About</span>
        </div>
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

    <div class="projectsContainer">
        <h2>Projects</h2>
        <div class="project" v-for="project in projects">
            <h3>{{project.title}}</h3>
            <div class="tech">
                <span v-for="tech in project.tech">{{tech}}</span>
            </div>
            <p>{{project.description}}</p>
            <div class="links">
                <a v-if="project.link" :href="project.link" target="_blank">Project</a>
                <a v-if="project.github" :href="project.github" target="_blank">Github</a>
            </div>
        </div>
    </div>

    <!-- https://maximpekarsky.com/
        https://www.andrewaskins.com/about/
        https://alexbainter.com/
    https://wattenberger.com/-->

    <!-- Get rid of top nav
        about is right on the home page
        projects are lower down on the home page
    blog is linked somewhere in about-->
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
                    title: "Misplaced Hashtags",
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
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr;
    text-align: center;
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

.projectsContainer {
    margin-top: 5em;
}

.project {
    background-color: #3C1F7B;
    width: 40%;
    margin: auto;
    border-radius: 5px;
    box-shadow: 0px 5px 4px #160b2e;
    padding: 1em;
    margin-bottom: 2em;
}

.tech span {
    background-color: blue;
    margin: 0 1em;
    border-radius: 10px;
    padding: 0.5em;
}
</style>