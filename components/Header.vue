<template>
  <nav ref="navBar" id="navbar" class="">
    <div class="r">

      <div class="c-4 xs-text-left xs-p1 flex flex-sitename">
        <div class="item">
          <nuxt-link class="sitename" to="/" exact>{{headerSiteName}}</nuxt-link>
        </div>
      </div>

      <div class="c-4 xs-border-top sm-border-top-none xs-p1">
        <div class="item xs-flex flex flex-social">
          <div class="social-item">
            <a href="https://www.linkedin.com/in/alvaro-belmonte">
              <svg class="social-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 50 50" width="50px" height="50px">    <path d="M41,4H9C6.24,4,4,6.24,4,9v32c0,2.76,2.24,5,5,5h32c2.76,0,5-2.24,5-5V9C46,6.24,43.76,4,41,4z M17,20v19h-6V20H17z M11,14.47c0-1.4,1.2-2.47,3-2.47s2.93,1.07,3,2.47c0,1.4-1.12,2.53-3,2.53C12.2,17,11,15.87,11,14.47z M39,39h-6c0,0,0-9.26,0-10 c0-2-1-4-3.5-4.04h-0.08C27,24.96,26,27.02,26,29c0,0.91,0,10,0,10h-6V20h6v2.56c0,0,1.93-2.56,5.81-2.56 c3.97,0,7.19,2.73,7.19,8.26V39z"/></svg>
            </a>
          </div>
          <div class="social-item">
            <a href="https://github.com/alvarobelmonte">
              <svg class="social-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 50 50" width="50px" height="50px">    <path d="M17.791,46.836C18.502,46.53,19,45.823,19,45v-5.4c0-0.197,0.016-0.402,0.041-0.61C19.027,38.994,19.014,38.997,19,39 c0,0-3,0-3.6,0c-1.5,0-2.8-0.6-3.4-1.8c-0.7-1.3-1-3.5-2.8-4.7C8.9,32.3,9.1,32,9.7,32c0.6,0.1,1.9,0.9,2.7,2c0.9,1.1,1.8,2,3.4,2 c2.487,0,3.82-0.125,4.622-0.555C21.356,34.056,22.649,33,24,33v-0.025c-5.668-0.182-9.289-2.066-10.975-4.975 c-3.665,0.042-6.856,0.405-8.677,0.707c-0.058-0.327-0.108-0.656-0.151-0.987c1.797-0.296,4.843-0.647,8.345-0.714 c-0.112-0.276-0.209-0.559-0.291-0.849c-3.511-0.178-6.541-0.039-8.187,0.097c-0.02-0.332-0.047-0.663-0.051-0.999 c1.649-0.135,4.597-0.27,8.018-0.111c-0.079-0.5-0.13-1.011-0.13-1.543c0-1.7,0.6-3.5,1.7-5c-0.5-1.7-1.2-5.3,0.2-6.6 c2.7,0,4.6,1.3,5.5,2.1C21,13.4,22.9,13,25,13s4,0.4,5.6,1.1c0.9-0.8,2.8-2.1,5.5-2.1c1.5,1.4,0.7,5,0.2,6.6c1.1,1.5,1.7,3.2,1.6,5 c0,0.484-0.045,0.951-0.11,1.409c3.499-0.172,6.527-0.034,8.204,0.102c-0.002,0.337-0.033,0.666-0.051,0.999 c-1.671-0.138-4.775-0.28-8.359-0.089c-0.089,0.336-0.197,0.663-0.325,0.98c3.546,0.046,6.665,0.389,8.548,0.689 c-0.043,0.332-0.093,0.661-0.151,0.987c-1.912-0.306-5.171-0.664-8.879-0.682C35.112,30.873,31.557,32.75,26,32.969V33 c2.6,0,5,3.9,5,6.6V45c0,0.823,0.498,1.53,1.209,1.836C41.37,43.804,48,35.164,48,25C48,12.318,37.683,2,25,2S2,12.318,2,25 C2,35.164,8.63,43.804,17.791,46.836z"/></svg>
            </a>
          </div>
          <div class="social-item">
            <a href="https://codepen.io/alvarobelmonte">
              <svg class="social-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 50 50" width="50px" height="50px"><path d="M 25 4 L 4 17.34375 L 4 32.652344 L 25 46 L 46 32.65625 L 46 17.34375 Z M 25 29.183594 L 19.066406 25.070313 L 25 21.023438 L 30.933594 25.070313 Z M 27 17.605469 L 27 9.949219 L 40.429688 18.484375 L 34.410156 22.65625 Z M 23 17.605469 L 15.589844 22.65625 L 9.570313 18.484375 L 23 9.949219 Z M 12.09375 25.042969 L 8 27.832031 L 8 22.203125 Z M 15.570313 27.453125 L 23 32.605469 L 23 40.050781 L 9.589844 31.527344 Z M 27 32.605469 L 34.429688 27.453125 L 40.410156 31.527344 L 27 40.050781 Z M 37.90625 25.042969 L 42 22.203125 L 42 27.832031 Z"/></svg>
            </a>
          </div>
        </div>

      </div>
      <div v-if="blogtitle" style="z-index:55;" class="c-12 xs-border-top xs-border-bottom xs-p2 xs-text-6 titlebar">
        <div class="item menu-links">
          <nuxt-link to="/" exact>Home</nuxt-link>
          <span v-show="crumb"> &nbsp;
            <span> > </span> &nbsp; {{thecrumb}} </span> &nbsp;
          <span> > </span> &nbsp; {{blogtitle}}
        </div>
      </div>
    </div>
  </nav>
</template>
<script>
import VueFuse from "~/components/VueFuse";
export default {
  props: ["blogtitle", "posts", "thecrumb"],
  data() {
    return {
      results: [],
      keys: [
        {
          name: "title",
          weight: 0.3
        },
        {
          name: "body",
          weight: 0.7
        }
      ],

      compResults: []
    };
  },
  components: { VueFuse },
  computed: {
    allPosts() {
      let posts = this.$store.state.blogPosts;
      let pages = this.$store.state.allPages;
      let both = posts.concat(pages);
      return both;
    },
    headerSiteName() {
      return this.$store.state.siteInfo.sitename;
    },
    componentResults() {
      return this.$store.state.results;
    },
     crumb() {
      return this.$store.state.theCrumb;
    }
  },

  methods: {

    navHeight() {
      var height = document.getElementById("navbar").clientHeight;
      console.log(height);
      this.$store.commit("SET_NAVHEIGHT", height - 1);
 
    }
  },

  mounted() {
    this.$on("searchChanged", results => {
      this.compResults = results;
    });
  },

  head () {
    return {
      link: [
        { rel: 'stylesheet', href: 'https://fonts.googleapis.com/css2?family=Titillium+Web:wght@600&display=swap' }
      ]
    }
  }
};
</script>
<style lang="scss">

.social-item {
  margin: 0 0.5rem;
}
.social-icon {
  fill: white;
  width: 2.8rem;
  transition: all 0.4s;
}

.social-icon:hover {
  transform: scale(1.25);
}

.flex{
  display: flex;

}
.flex-social {
  justify-content: center;
  align-items: center;
}
.flex-sitename {
  justify-content: start;
  align-items: center;
}
#navbar {z-index:999;}
.titlebar .item {
  overflow-x: none;
}
.results {
  padding-left: 0;
  transform: translateY(17px);
  width: 30vw;
}
.results li {
  list-style-type: none;
  margin-left: 0;
}
nav {
  padding-top: 1rem;
  position: fixed;
  background: var(--color-primary);
  top: 0;
  left: 0;
  right: 0;
}
.sitename {
  color: white;
  font-family: 'Titillium Web', sans-serif;
  padding-left: 2rem;
  font-weight: 400;
  font-size: 1.8rem;

  &:hover {
    color: white;
    opacity: 85%;
  }
}

.item {
  flex: start;
}

.menu-links {
  color: #ccc;
}

a {
  color: #fff;
}

a:hover {
  color: #ccc;
}

@media only screen and (max-width: 54rem) {
  .social-icon {
    width: 1.5rem;
  }
  .sitename {
    font-size: 1.1rem;
  }
}
</style>