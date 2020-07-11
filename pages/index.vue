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
        <Card  :projects="allProjectPosts"/>
    </section>

    </main>
</template>

<script>
import BaelGrid from "~/components/BaelGrid";
import FullGrid from "~/components/FullGrid";
import Card from "~/components/Card";

export default {
    watchQuery: ['page'],

   transition (to, from) {
     
    if (!from) return 'fade'
    return +to.query.page > +from.query.page ? 'slide-right' : 'slide-left'
  },
  name: "Index",
  components: { BaelGrid, FullGrid, Card },
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
    color: var(--color-primary);
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
      font-family: 'Titillium Web', sans-serif;
    padding: 1rem;
  }
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
