<template>
    <main>
    <!--<component :is="getLayout" :allitems="allBlogPosts"></component> -->
    <div class="main-content">
        <div class="bg-video">
            <video class="bg-video__content" poster="~/static/images/mine/frame.jpg" autoplay muted loop>
              <source src="~/static/images/mine/video.webm" type="video/webm"> Your browser is not supported
            </video>
        </div>

    </div>
    <section class="portfolio">
        <h1>PORTFOLIO</h1>
        <div class="card" v-for="project in allProjectPosts">
          <div class="thumbnail">
            <transition appear name="fade"><img class="thumbnail featured-image" :src="project.thumbnail" :alt="title"></transition>
          </div>
          <div class="info">
            <h2 class="title">{{project.title}}</h2>
            <p>{{project.description}}</p>
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
  methods: {},

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
  opacity: 0.65;
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
  background-color: rgb(189, 189, 189);
  height: 25rem;
  border-radius: 3rem;
  width: 50%;
  margin: 2rem auto;
  display: flex;

  .thumbnail {
    flex: 50%;
  }

  .info {
    padding: 4rem 3rem;
    flex: 50%;
  }
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
