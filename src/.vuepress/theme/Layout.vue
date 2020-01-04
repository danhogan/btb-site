<template>
  <div
    class="theme-container"
    :class="pageClasses"
    @touchstart="onTouchStart"
    @touchend="onTouchEnd"
  >
    <Navbar v-if="shouldShowNavbar" @toggle-sidebar="toggleSidebar"/>

    <div class="sidebar-mask" @click="toggleSidebar(false)"></div>

    <Sidebar :items="sidebarItems" @toggle-sidebar="toggleSidebar">
      <slot name="sidebar-top" slot="top"/>
      <slot name="sidebar-bottom" slot="bottom"/>
    </Sidebar>

    <!-- <div v-if="$page.frontmatter.extras">
        <MySidebar class="mySidebar mySidebarRight" :categories="categories.slice(5,10)"></MySidebar>
        <MySidebar class="mySidebar mySidebarLeft" :categories="categories.slice(0,5)"></MySidebar>
    </div> -->

    <Blog v-if="$frontmatter.blog" :sidebar-items="sidebarItems"/>

    <div class="custom-layout" v-else-if="$page.frontmatter.layout">
      <component :is="$page.frontmatter.layout"/>
    </div>

    <Home v-else-if="$page.frontmatter.home"/>

    <Page v-else :sidebar-items="sidebarItems">
      <slot name="page-top" slot="top"/>
      <slot name="page-bottom" slot="bottom"/>
    </Page>

    <SWUpdatePopup :updateEvent="swUpdateEvent"/>
  </div>
</template>

<script>
import Vue from "vue";
import nprogress from "nprogress";
import Blog from "./layout/Blog.vue";
import Home from "./layout/Home.vue";
import Page from "./layout/Page.vue";
import Navbar from "./components/Navbar.vue";
import Sidebar from "./components/Sidebar.vue";
import MySidebar from "./components/MySidebar.vue";
import SWUpdatePopup from "./components/SWUpdatePopup.vue";
import { resolveSidebarItems } from "./util";

export default {
  components: {
    Blog,
    Home,
    Page,
    Sidebar,
    Navbar,
    SWUpdatePopup,
    MySidebar
  },

  data() {
    return {
      isSidebarOpen: false,
      swUpdateEvent: null,

      //this will have to change from month to month
        categories: [
            {
                category: 'Runs',
                value: 234,
                udlTeam: 'Riptide',
                udlTeamLogo: 'https://img.fantrax.com/logos/tmLogo_q9qkntnviwcl7gnr_512.jpg',
                playerName: 'Billy Bob',
                playerImage: 'https://www.thetimes.co.uk/imageserver/image/methode%2Ftimes%2Fprod%2Fweb%2Fbin%2F330e2668-4a87-11e9-9ce9-2870f730ce44.jpg?crop=1600%2C900%2C0%2C0&resize=685'
            },
            {
                category: 'Home Runs',
                value: 234,
                udlTeam: 'Riptide',
                udlTeamLogo: 'https://img.fantrax.com/logos/tmLogo_q9qkntnviwcl7gnr_512.jpg',
                playerName: 'Billy Bob',
                playerImage: 'https://www.thetimes.co.uk/imageserver/image/methode%2Ftimes%2Fprod%2Fweb%2Fbin%2F330e2668-4a87-11e9-9ce9-2870f730ce44.jpg?crop=1600%2C900%2C0%2C0&resize=685'
            },
            {
                category: 'RBI',
                value: 234,
                udlTeam: 'Riptide',
                udlTeamLogo: 'https://img.fantrax.com/logos/tmLogo_q9qkntnviwcl7gnr_512.jpg',
                playerName: 'Billy Bob',
                playerImage: 'https://www.thetimes.co.uk/imageserver/image/methode%2Ftimes%2Fprod%2Fweb%2Fbin%2F330e2668-4a87-11e9-9ce9-2870f730ce44.jpg?crop=1600%2C900%2C0%2C0&resize=685'
            },
            {
                category: 'Stolen Bases',
                value: 234,
                udlTeam: 'Riptide',
                udlTeamLogo: 'https://img.fantrax.com/logos/tmLogo_q9qkntnviwcl7gnr_512.jpg',
                playerName: 'Billy Bob',
                playerImage: 'https://www.thetimes.co.uk/imageserver/image/methode%2Ftimes%2Fprod%2Fweb%2Fbin%2F330e2668-4a87-11e9-9ce9-2870f730ce44.jpg?crop=1600%2C900%2C0%2C0&resize=685'
            },
            {
                category: 'OBP',
                value: 234,
                udlTeam: 'Riptide',
                udlTeamLogo: 'https://img.fantrax.com/logos/tmLogo_q9qkntnviwcl7gnr_512.jpg',
                playerName: 'Billy Bob',
                playerImage: 'https://www.thetimes.co.uk/imageserver/image/methode%2Ftimes%2Fprod%2Fweb%2Fbin%2F330e2668-4a87-11e9-9ce9-2870f730ce44.jpg?crop=1600%2C900%2C0%2C0&resize=685'
            },
            {
                category: 'Strikeouts',
                value: 234,
                udlTeam: 'Riptide',
                udlTeamLogo: 'https://img.fantrax.com/logos/tmLogo_q9qkntnviwcl7gnr_512.jpg',
                playerName: 'Billy Bob',
                playerImage: 'https://www.thetimes.co.uk/imageserver/image/methode%2Ftimes%2Fprod%2Fweb%2Fbin%2F330e2668-4a87-11e9-9ce9-2870f730ce44.jpg?crop=1600%2C900%2C0%2C0&resize=685'
            },
            {
                category: 'Quality Starts',
                value: 234,
                udlTeam: 'Riptide',
                udlTeamLogo: 'https://img.fantrax.com/logos/tmLogo_q9qkntnviwcl7gnr_512.jpg',
                playerName: 'Billy Bob',
                playerImage: 'https://www.thetimes.co.uk/imageserver/image/methode%2Ftimes%2Fprod%2Fweb%2Fbin%2F330e2668-4a87-11e9-9ce9-2870f730ce44.jpg?crop=1600%2C900%2C0%2C0&resize=685'
            },
            {
                category: 'ERA',
                value: 234,
                udlTeam: 'Riptide',
                udlTeamLogo: 'https://img.fantrax.com/logos/tmLogo_q9qkntnviwcl7gnr_512.jpg',
                playerName: 'Billy Bob',
                playerImage: 'https://www.thetimes.co.uk/imageserver/image/methode%2Ftimes%2Fprod%2Fweb%2Fbin%2F330e2668-4a87-11e9-9ce9-2870f730ce44.jpg?crop=1600%2C900%2C0%2C0&resize=685'
            },
            {
                category: 'WHIP',
                value: 234,
                udlTeam: 'Riptide',
                udlTeamLogo: 'https://img.fantrax.com/logos/tmLogo_q9qkntnviwcl7gnr_512.jpg',
                playerName: 'Billy Bob',
                playerImage: 'https://www.thetimes.co.uk/imageserver/image/methode%2Ftimes%2Fprod%2Fweb%2Fbin%2F330e2668-4a87-11e9-9ce9-2870f730ce44.jpg?crop=1600%2C900%2C0%2C0&resize=685'
            },
            {
                category: 'Saves + Holds',
                value: 234,
                udlTeam: 'Riptide',
                udlTeamLogo: 'https://img.fantrax.com/logos/tmLogo_q9qkntnviwcl7gnr_512.jpg',
                playerName: 'Billy Bob',
                playerImage: 'https://www.thetimes.co.uk/imageserver/image/methode%2Ftimes%2Fprod%2Fweb%2Fbin%2F330e2668-4a87-11e9-9ce9-2870f730ce44.jpg?crop=1600%2C900%2C0%2C0&resize=685'
            }
        ]
    };
  },

  computed: {
    shouldShowNavbar() {
      const { themeConfig } = this.$site;
      const { frontmatter } = this.$page;
      if (frontmatter.navbar === false || themeConfig.navbar === false) {
        return false;
      }
      return (
        this.$title ||
        themeConfig.logo ||
        themeConfig.repo ||
        themeConfig.nav ||
        this.$themeLocaleConfig.nav
      );
    },

    shouldShowSidebar() {
      const { frontmatter } = this.$page;
      return (
        !frontmatter.layout &&
        !frontmatter.home &&
        frontmatter.sidebar !== false &&
        this.sidebarItems.length
      );
    },

    sidebarItems() {
      return resolveSidebarItems(
        this.$page,
        this.$route,
        this.$site,
        this.$localePath
      );
    },

    pageClasses() {
      const userPageClass = this.$page.frontmatter.pageClass;
      return [
        {
          "no-navbar": !this.shouldShowNavbar,
          "sidebar-open": this.isSidebarOpen,
          "no-sidebar": !this.shouldShowSidebar
        },
        userPageClass
      ];
    },
  },

  mounted() {
    window.addEventListener("scroll", this.onScroll);

    // configure progress bar
    nprogress.configure({ showSpinner: false });

    this.$router.beforeEach((to, from, next) => {
      if (to.path !== from.path && !Vue.component(to.name)) {
        nprogress.start();
      }
      next();
    });

    this.$router.afterEach(() => {
      nprogress.done();
      this.isSidebarOpen = false;
    });

    this.$on("sw-updated", this.onSWUpdated);
  },

  methods: {
    toggleSidebar(to) {
      this.isSidebarOpen = typeof to === "boolean" ? to : !this.isSidebarOpen;
    },

    // side swipe
    onTouchStart(e) {
      this.touchStart = {
        x: e.changedTouches[0].clientX,
        y: e.changedTouches[0].clientY
      };
    },

    onTouchEnd(e) {
      const dx = e.changedTouches[0].clientX - this.touchStart.x;
      const dy = e.changedTouches[0].clientY - this.touchStart.y;
      if (Math.abs(dx) > Math.abs(dy) && Math.abs(dx) > 40) {
        if (dx > 0 && this.touchStart.x <= 80) {
          this.toggleSidebar(true);
        } else {
          this.toggleSidebar(false);
        }
      }
    },

    onSWUpdated(e) {
      this.swUpdateEvent = e;
    }
  }
};
</script>

<style src="prismjs/themes/prism-tomorrow.css"></style>
<style src="./styles/theme.styl" lang="stylus"></style>

<style>
    .mySidebar {
        box-shadow: 0 8px 12px 0 hsla(0, 0%, 0%, 0.2);
        padding: 0 2em;
    }

    .mySidebarLeft {
        float: left;
    }

    .mySidebarRight {
        float: right;
    }

    @media only screen and (max-width: 600px) {
        .mySidebar {
            float: none;
        }
    }  
</style>

