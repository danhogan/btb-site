<template>
  <div class="home">
    <link href="https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet" integrity="sha384-wvfXpqpZZVQGK6TAh5PVlGOfQNHSoD2xbE+QkPxCAFlNEevoEH3Sl0sibVcOQVnN" crossorigin="anonymous">
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
    
}
</script>

<style>
body {
    background-color: #281552;
    color: #ccc;
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
}

h2 {
  font-size: 2em;
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
</style>