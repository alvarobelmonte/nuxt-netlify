<template>
    <main>
    <!--<component :is="getLayout" :allitems="allBlogPosts"></component> -->
    <div class="main-content">
        <div class="bg-video">
            <video class="bg-video__content" poster="~/static/images/mine/frame.jpg" autoplay muted loop>
              <source src="~/static/images/mine/video.webm" type="video/webm"> Your browser is not supported
            </video>
        </div>
        <h1><b>Hi, I'm a <span class="fucsia">Web Developer</span>&#128187; based in <span class="fucsia"> Alicante</span>&#127796;</b></h1>
          <div class="profile-picture">
              <img src="~/static/images/uploads/profile.jpg" width="" height="" alt="Profile picture of Alvaro Belmonte." class="img">
          </div>

    </div>
    <section class="portfolio">
        <h1>&#128193; PORTFOLIO</h1>
        <div class="card" v-for="project in allProjectPosts">
          <div class="thumbnail">
            <div :style="thumbnailCard(project.thumbnail)" ></div>
          </div>
          <div class="info">
            <div class="info-content">
              <h1 class="title">{{project.title}}</h1>
              <p>{{project.description}}</p>
              <div class="stack">
                <h2>Technologies used</h2>
                <div class="stack-container">
                  <img v-for="tech in project.technologies" class="stack-image" :src="tech" :alt="tech">
                </div>
              </div>
              <a class="project-link" :href="project.source">Source Code</a>
              <a class="project-link" :href="project.demo">Demo</a>


            </div>
          </div>
        </div>
    </section>

    </main>
</template>

<script>
import BaelGrid from "~/components/BaelGrid";
import FullGrid from "~/components/FullGrid";
export default {
    watchQuery: ['page'],

   transition (to, from) {
     
    if (!from) return 'fade'
    return +to.query.page > +from.query.page ? 'slide-right' : 'slide-left'
  },
  name: "Index",
  components: { BaelGrid,FullGrid },
  data() {
    return {};
  },
  methods: {
    thumbnailCard(thumb) {
      return {
        "width": "100%",
        "height": "100%",
        "background-image": "url("+thumb+")",
        //"background-size": "100%",
        "background-repeat": "no-repeat",
        "background-size": "100% 100%"
      }
    },
  },

  computed: {
    allBlogPosts() {
      return this.$store.state.blogPosts;
    },
    allProjectPosts() {
      return this.$store.state.projectPosts;
    },

    getLayout() {
if (this.$store.state.siteInfo.altlayout == false ) {
  return 'BaelGrid'
} else if (this.$store.state.siteInfo.altlayout == true ) {
  return 'FullGrid'
}

    }
  }
};
</script>

<style lang="scss">
.bg-video {

  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  /*z-index: -1;
  opacity: 0.65;
  overflow: hidden;
  display: none;
  visibility: hidden;*/
  opacity: 0.35;
  &__content {
    height: 100%;
    width: 100%;
    object-fit: cover;
  }

}

.main-content {
  min-width: 100vw;
  min-height: 75vh;
  padding-top: 10rem;

  position: relative;
  background-image: linear-gradient(
    to right bottom,
    rgba(blue, 0.5),
    rgba(green, 0.5)
  );
  
  h1 {
    text-align: center;
    color: black;
    background-color: white;
    padding: 1rem;
  }
}

.video {
    background-image: linear-gradient(
    to right bottom,
    rgba(blue, 0.5),
    rgba(purple, 0.5)
  );
  max-width: 100%;
  min-height: 100vh;
}

.portfolio {
  padding-top: 3rem;
  padding-bottom: 5rem;
  h1 {
    text-align: center; 
    font-size: 3rem;
    font-family: 'Space Mono', monospace;
    padding: 1rem;
  }
}

.card {
  background-color:white;
  height: 25rem;
  border-radius: 1rem;
  width: 50%;
  margin: 2rem auto;
  display: flex;
  overflow: hidden;

  transition: all 0.3s;

  -webkit-box-shadow: 0 2rem 5rem rgba(0,0,0,.1);
  -moz-box-shadow: 0 2rem 5rem rgba(0,0,0,.1);
  box-shadow: 0 2rem 5rem rgba(0,0,0,.1);

  .thumbnail {
    flex: 50%;
    background-color: transparent;
  }

  .info {
    padding: 2rem 3rem;
    flex: 50%;

    .info-content {

    }

    .stack-container{
      padding: 1rem;
    }

    .stack-image {
      width: 2rem;
      height: 2rem;
      margin: 0.4rem;
    }

    .project-link {
      text-align: center;
      color: black;
      padding: 0.4rem;
      display: block;
      border: 1px solid black;
      margin: 0.5rem 0;

      &:hover {
        background-color: black;
        color: white;
      }
    }
  }

  h1 {
    font-family: 'Space Mono', monospace;
    font-size: 1.3rem;
    background-color: black;
    color: white;
    border-radius: 0.6rem;
    padding: 0.4rem;
  }
  h2 {
    font-family: 'Space Mono', monospace;
    font-size: 1.1rem;
  }

}

.card:hover {
    transform: scale(1.02);
    cursor: pointer;
}

.fucsia {
  color: rgb(255, 0, 157);
}



.profile-picture .img{
  border-radius: 50%;
  display: flex;
  margin: 1rem auto;
  width: 15rem;


}



.browse a {
  width: 100%;
}
.search:focus {
  outline: none;
}
.footer__heading {
  text-transform: uppercase;
}
nav .r {
  grid-gap: 0;
}
.r.full-height {
  grid-gap: 0;
}
@media only screen and (max-width: 40rem) {
  .xs-collapse {
    visibility: hidden;
    visibility: collapse;
    border: 0 !important;
    border-color: none !important;
    padding: 0 !important;
  }
  .xs-visible {
    visibility: visible;
  }
}
</style>
