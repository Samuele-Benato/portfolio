<script>
import simpleIcons from "simple-icons";
export default {
  title: "Column1",
  emits: ["hoverIn", "hoverOut"],
  data() {
    return {
      i: {
        linkedin: simpleIcons.Get("linkedin").svg,
        github: simpleIcons.Get("github").svg,
      },
    };
  },
};
</script>

<template>
  <div class="column">
    <div class="center">
      <h1>Mi presento</h1>
      <p>
        Mi chiamo Samuele, mi sono interfacciato al mondo tech da relativamente poco ma ho una gran voglia di migliorare e ampliare le mie conoscenze, oltre ai pilastri 
        <a
          href="https://it.wikipedia.org/wiki/HTML5"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
          >HTML5</a
        >,
        e 
        <a
          href="https://it.wikipedia.org/wiki/CSS"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
          >CSS3</a
        > ho avuto la possibilità di sperimentare i seguenti linguaggi / framework : <br><br>
        <a
          href="https://it.wikipedia.org/wiki/JavaScript"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
          >JavaScript</a
        >,
        <a
          href="https://getbootstrap.com/"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
          >Bootstrap</a
        >,
        <a
          href="https://vitejs.dev/"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
          >Vite</a
        >,
        <a
          href="https://vuejs.org"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
          >Vue</a
        >,
        <a
          href="https://nodejs.org/"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
          >Node.js</a
        >,
        <a
          href="https://sass-lang.com/"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
          >Sass</a
        >,
        ,
        <a
          href="https://it.wikipedia.org/wiki/PHP"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
          >Php</a
        >,
        <a
          href="https://laravel.com/docs/9.x"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
          >Laravel 9.x</a
        >.<br /><br />
       <p>Beh, ormai abbiamo rotto il ghiaccio ora puoi dare un occhiata ai </p>
        <router-link
          to="/projects"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
          class="special-link"
          >progetti</router-link
        >
        o ai
        <router-link
          to="/contact"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
          class="special-link"
          >contatti</router-link
        >.
      </p>
      <div class="socials">
        <a
          v-html="i.linkedin"
          href="https://www.linkedin.com/in/samuele-benato-a9615a29b/"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
        ></a>
        <a
          v-html="i.github"
          href="https://github.com/Samuele-Benato"
          @mouseenter="$emit('hoverIn')"
          @mouseleave="$emit('hoverOut')"
        ></a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.column {
  background: var(--bg-primary);
  display: grid;
  justify-content: center;
  align-items: center;
  transition: background 0.2s;
}

.center {
  margin: 1rem auto;
  max-width: 480px;
  padding: 1rem 2.5rem;
}

h1 {
  color: var(--accent);
  font-size: 4rem;
  line-height: 1em;
  margin-bottom: 0.2em;
  opacity: 0;
  transform-style: preserve-3d;
  transform-origin: top center;
  transform: var(--animation-initial);
  animation: var(--animation);
  animation-delay: 0.1s;
}

p {
  opacity: 0;
  transform-style: preserve-3d;
  transform-origin: top center;
  transform: var(--animation-initial);
  animation: var(--animation);
  animation-delay: 0.2s;
  color: var(--text-primary);
  transition: color 0.2s;
}

p > a {
  color: inherit;
  font-weight: 500;
  transition: color 0s;
}

.special-link {
  color: var(--accent);
}

.socials {
  margin-top: 1.5em;
  opacity: 0;
  transform-style: preserve-3d;
  transform-origin: top center;
  transform: var(--animation-initial);
  animation: var(--animation);
  animation-delay: 0.5s;
}

.socials a {
  fill: var(--text-secondary);
  text-decoration: none;
  margin-right: 1.2rem;
  transition: 0.2s;
}

.socials a:hover {
  fill: var(--accent);
}

@media only screen and (max-width: 510px) {
  h1 {
    font-size: 2.5rem;
  }
}
</style>
