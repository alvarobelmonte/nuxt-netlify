<template>

    <div>
        <div class="card" v-for="project in projects" :key="project.id">
            <div class="thumbnail">
                <div :style="thumbnailCard(project.thumbnail)" ></div>
            </div>
            <div class="info">
                <div class="info-content">
                    <h1 class="title">{{project.title}}</h1>
                    <p class="description">{{project.description}}</p>
                    <div class="stack">
                        <h2 class="subtitle">Technologies used</h2>
                        <div class="stack-container">
                            <img v-for="tech in project.technologies" :key="tech.id" class="stack-image" :src="tech" :alt="tech">
                        </div>
                    </div>
                    <a class="project-link" :href="project.source">Code</a>
                    <a class="project-link" :href="project.demo">Demo</a>
                </div>
            </div>
        </div>
    </div>

</template>

<script>
export default {
    props: {
        projects: Array
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
    head () {
        return {
        link: [
            { rel: 'stylesheet', href: 'https://fonts.googleapis.com/css2?family=Ubuntu&display=swap' }
        ]
        }
    }
};
</script>

<style lang="scss">


.card {
  background-color:white;
  height: 38rem;
  border-radius: 1rem;
  width: 90%;
  margin: 2rem auto;
  display: flex;
  flex-direction: column;
  overflow: hidden;

  transition: all 0.3s;

  -webkit-box-shadow: 0 2rem 5rem rgba(0,0,0,.1);
  -moz-box-shadow: 0 2rem 5rem rgba(0,0,0,.1);
  box-shadow: 0 2rem 5rem rgba(0,0,0,.1);

  .thumbnail {
    min-height: 12rem;
    flex: 1;
  }

  .info {
    padding: 1rem 3rem;
    flex: 1;


    .title {
        font-family: 'Ubuntu', sans-serif;
        font-size: 1rem;
        background-color: var(--color-primary);
        color: white;
        border-radius: 0.6rem;
        padding: 0.4rem;
    }
    .subtitle {
        font-family: 'Ubuntu', sans-serif;
        font-size: 1.1rem;
    }

    .description {
        padding: 0.3rem 0;
    }


    .stack-container{
      padding: 1rem;
    }

    .stack-image {
      width: 2rem;
      height: 2rem;
      margin: 0.1rem;
    }

    .project-link {
      text-align: center;
      color: var(--color-primary);
      padding: 0.4rem;
      display: block;
      border: 1px solid var(--color-primary);
      margin: 0.5rem 0;

      &:hover {
        background-color: var(--color-primary);
        color: white;
      }
    }
  }



  &:hover {
    transform: scale(1.02);
    cursor: pointer;
  }
}


@media only screen and (min-width: 600px) {

    .stack-image {
      min-width: 4rem;
      min-height: 4rem;
      padding: 0.1rem;
    }
}

@media only screen and (min-width: 1200px) {
    .card {
        width: 50%;
        flex-direction: row;
        height: 27rem;
    }
    .thumbnail {
        flex: 50%;
        height: 100%;
    }
    .info {
        flex: 50%;
    }
    .stack-image {
      min-width: 2.4rem;
      min-height: 2.4rem;
      padding: 0.1rem;
    }
    .description {
        padding: 1rem 0;
    }
}

</style>
