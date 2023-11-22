<script>
import NavBar from "../components/NavBar.vue";
let images = [];
const projects = [
  {
    name: "Campo Minato",
    image: "/assets/projects/campoMinato.jpg",
    subtitle: "Un semplice gioco il cui obbiettivo è fare più passi possibili prima di fare BOOM!",
    url: "https://github.com/Samuele-Benato/js-campominato-dom",
  },
  {
    name: "FizzBuzz",
    image: "/assets/projects/fizzBuzz.jpg",
    subtitle: "Pratica con Javascript, obbiettivo è sostituire i multipli di 3 con Fizz, i multipli di 5 con Buzz e i multipli in comune con FizzBuzz",
    url: "https://github.com/Samuele-Benato/js-fizzbuzz",
  },
  {
    name: "Boolzapp",
    image: "/assets/projects/boolzapp.jpg",
    subtitle: "Riproduzione della consolidata app con inserimento di filtri di ricerca, risposta automatica al messaggio e memorizzazione della chat",
    url: "https://github.com/Samuele-Benato/vue-boolzapp",
  },
  {
    name: "Boolfix",
    image: "/assets/projects/boolfix.jpg",
    subtitle: "Riproduzione della famosa app con inserimento di chiamata esterna api",
    url: "https://github.com/Samuele-Benato/vite-boolflix",
  },
  {
    name: "Layout Concessionario",
    image: "/assets/projects/carLayout.jpg",
    subtitle: "Riproduzione di un possibile layout mono pagina di un concessionario",
    url: "https://github.com/Samuele-Benato/htmlcss-responsive-layout",
  },
  {
    name: "DC COMICS",
    image: "/assets/projects/dcComics.jpg",
    subtitle: "Esercitazione di grafica riproducendo il noto sito",
    url: "https://github.com/Samuele-Benato/vite-comics",
  },
  {
    name: "Spotify",
    image: "/assets/projects/spotify.jpg",
    subtitle: "Esercitazione di grafica con effetti hover (visualizzazione web)",
    url: "https://github.com/Samuele-Benato/html-css-spotifyweb",
  },
  {
    name: "Back Office",
    image: "/assets/projects/backOffice.jpg",
    subtitle: "Struttura in PHP utilizzando Laravel 9.x la quale comprende tutte le viste dei controller, soft delete e restore",
    url: "https://github.com/Samuele-Benato/laravel-api",
  },
  {
    name: "Front Office",
    image: "/assets/projects/frontOffice.jpg",
    subtitle: "Struttura in Vue.js collegata al back office per la visualizzazione dell'utente, comprende filtri di ricerca per categoria",
    url: "https://github.com/Samuele-Benato/vite-boolfolio",
  },
  {
    name: "Vedi altro",
    image: "/assets/projects/github.jpg",
    subtitle: "Qui il link al mio profilo Github!",
    url: "https://github.com/Samuele-Benato",
  },
];
export default {
  title: "Projects",
  emits: ["hoverIn", "hoverOut"],
  components: {
    NavBar,
  },
  data() {
    return {
      projects,
      loaded: false,
    };
  },
  mounted() {
    let loadCount = 0;
    const checkForLoad = () => {
      if (loadCount == projects.length) {
        this.loaded = true;
        console.log("Loaded!");
      }
    };
    const preloadImage = (url) => {
      let img = new Image();
      img.src = url;
      img.addEventListener("load", () => {
        loadCount++;
        checkForLoad();
      });
      images.push(img);
      return;
    };
    projects.forEach((project, i) => {
      preloadImage(project.image);
    });
  },
  methods: {
    open(u) {
      window.open(u);
    },
  },
};
</script>

<template>
  <main>
    <h1 class="background">Projects</h1>
      <!-- <img src="public/assets/projects/logoSB.PNG" class="spinner rotate" /> -->
    <NavBar @hoverIn="$emit('hoverIn')" @hoverOut="$emit('hoverOut')" />
    <div class="project-grid">
      <a
        class="project-link"
        :href="p.url"
        @click.prevent
        v-for="p in projects"
      >
        <div
          class="project"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
          @click="open(p.url)"
        >
          <img :src="p.image" class="project-image" v-if="loaded" />
          <div class="project-image skeleton" v-else></div>
          <h2>{{ p.name }}</h2>
          <p>{{ p.subtitle }}</p>
        </div>
      </a>
    </div>
  </main>
</template>

<style scoped>
.project-grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  width: 95vw;
  margin: 2.5vw;
  margin-top: 4rem;
}

.project {
  margin: auto;
  margin-top: 2rem;
  cursor: inherit;
}

.project-image {
  max-width: 20rem;
  max-height: 15rem;
  aspect-ratio: 20 / 15;
  object-fit: cover;
  border-radius: 0.3rem;
  transition: 0.2s;
  box-shadow: 0 3px 5px rgba(0, 0, 0, 0.3);
}

.project p{
  padding-right: 1.75rem;
}

.project-image.skeleton {
  position: relative;
  overflow: hidden;
  background-color: #ffffff;
}

.project-image.skeleton:after {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  transform: translateX(-100%);
  background-image: linear-gradient(
    90deg,
    rgba(225, 225, 225, 0) 0,
    rgba(225, 225, 225, 0.2) 20%,
    rgba(225, 225, 225, 0.5) 60%,
    rgba(225, 225, 225, 0)
  );
  animation: shimmer 2s infinite;
  content: "";
}

@keyframes shimmer {
  100% {
    transform: translateX(100%);
  }
}

.project:hover .project-image {
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
  filter: grayscale(1);
}

.project h2 {
  color: var(--text-primary);
  position: relative;
  margin-right: 0;
  width: max-content;
  transition: color 0.2s;
}

.project h2:before {
  content: "";
  display: block;
  background: var(--accent);
  max-height: 0;
  position: absolute;
  bottom: 0.2em;
  left: 0;
  height: 100%;
  width: 100%;
  border-radius: 0.1em;
  transition: max-height 0.2s;
  z-index: -1;
}

.project:hover h2 {
  color: white;
}

.project:hover h2:before {
  max-height: 1em;
}

.project p {
  color: var(--text-secondary);
}

.project-link {
  text-decoration: none;
}

.background {
  color: var(--accent);
  position: fixed;
  z-index: -1;
  bottom: 0;
  left: 2rem;
  font-size: 30vh;
  opacity: 0.1;
  transform: skewX(-10deg);
  user-select: none;
}


/* .spinner {
  position: fixed;
  bottom: calc(18px + 32px);
  right: calc(18px + 32px);
  width: 17rem;
  max-width: 30vw;
  transform: translate(50%, -50%);
}

.rotate {
  animation: rotate 90s infinite linear;
  transform-origin: bottom right;
}

@keyframes rotate {
  0% {
    transform: rotate(0) translate(50%, 50%);
  }
  100% {
    transform: rotate(360deg) translate(50%, 50%);
  }
} */


@media only screen and (max-width: 1680px) {
  .project-grid {
    grid-template-columns: 1fr 1fr 1fr 1fr;
  }
}

@media only screen and (max-width: 1360px) {
  .project-grid {
    grid-template-columns: 1fr 1fr 1fr;
  }

  /* .spinner {
    display: none;
  } */
}

@media only screen and (max-width: 1041px) {
  /* .spinner {
    display: none;
  } */
  .project-grid {
    grid-template-columns: 1fr 1fr;
  }

  .project-link:last-of-type {
    margin-bottom: 4rem;
  }

  .project p {
    display: none;
  }
}

@media only screen and (max-width: 735px) {
  /* .spinner {
    display: none;
  } */
  .project-grid {
    grid-template-columns: 1fr;
    margin-top: 6rem;
  }

  .project {
    width: max-content;
    margin: auto;
    margin-bottom: 1rem;
  }

  .project-image {
    width: 80vw !important;
    height: 11rem;
  }

  .project p {
    display: none;
  }
}
</style>
