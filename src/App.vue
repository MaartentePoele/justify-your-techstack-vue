<script setup>
import ThemeSwitch from "./components/ThemeSwitch.vue";
</script>

<template>
  <article>
    <ThemeSwitch />
    <figure>
      <picture>
        <source
          type="image/avif"
          srcset="
            https://fdnd.directus.app/assets/ee9e43f9-4b86-4969-bbf9-b36a223ef9ca?format=avif&height=550
          "
        />
        <source
          type="image/webp"
          srcset="
            https://fdnd.directus.app/assets/ee9e43f9-4b86-4969-bbf9-b36a223ef9ca?format=webp&height=550
          "
        />
        <img
          src="https://fdnd.directus.app/assets/ee9e43f9-4b86-4969-bbf9-b36a223ef9ca?height=550"
          alt="Profielfoto van Maarten te Poele"
          fetchpriority="high"
          width="250"
          height="250"
        />
      </picture>
    </figure>

    <h1>Maarten te Poele</h1>
    <h2>Frontend Developer</h2>
    <ul>
      <li>
        <PhoneIcon />
        06-12345678
      </li>
      <li>
        <EmailIcon />
        maarten.te.poele@hva.nl
      </li>
      <li>
        <a href="https://github.com/MaartentePoele/i-love-web" target="_blank">
          <WebsiteIcon />
          Portfolio
        </a>
      </li>
      <li>
        <a
          href="https://www.linkedin.com/in/maarten-te-poele-3a7a57332/"
          target="_blank"
        >
          <LinkedinIcon />
          LinkedIn
        </a>
      </li>
      <li>
        <a href="https://github.com/MaartentePoele" target="_blank">
          <GithubIcon />
          GitHub
        </a>
      </li>
    </ul>

    <div class="hover-wrapper">
      <div class="hover top-left"></div>
      <div class="hover top-center"></div>
      <div class="hover top-right"></div>
      <div class="hover middle-left"></div>
      <div class="hover middle-center"></div>
      <div class="hover middle-right"></div>
      <div class="hover bottom-left"></div>
      <div class="hover bottom-center"></div>
      <div class="hover bottom-right"></div>
    </div>
  </article>
</template>

<style scoped>
article {
  background-color: var(--bg);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
  display: grid;
  grid-template-areas:
    "figure"
    "name"
    "job"
    "links";
  grid-template-rows: max-content max-content max-content 1fr;
  height: 100dvh;
  justify-items: center;
  position: relative;
  transform-style: preserve-3d;
  transition: transform 0.3s ease-out;

  @media (min-width: 800px) {
    aspect-ratio: 1.6 / 1;
    grid-template-areas:
      "figure name"
      "figure job"
      "figure links";
    grid-template-columns: 1fr 1fr;
    grid-template-rows: max-content max-content 1fr;
    height: clamp(400px, 33.33vw, 600px);
    justify-items: start;
  }
}

figure {
  background: linear-gradient(
    var(--primary),
    var(--primary) 50%,
    var(--bg) 50%
  );
  display: grid;
  grid-area: figure;
  padding: 2rem 0;
  place-items: center;

  @media (min-width: 800px) {
    background: linear-gradient(
      to right,
      var(--primary),
      var(--primary) 50%,
      var(--bg) 50%
    );
  }

  picture {
    display: flex;
    justify-content: center;

    img {
      aspect-ratio: 1;
      border-radius: 50%;
      height: auto;
      object-fit: cover;
      width: clamp(225px, 75%, 250px);
    }
  }
}

h1 {
  color: var(--content);
  grid-area: name;

  @media (min-width: 800px) {
    padding-top: clamp(2rem, 5.33vw, 4rem);
  }
}

h2 {
  grid-area: job;
  font-weight: normal;
}

ul {
  align-content: center;
  display: grid;
  gap: 1.5rem;
  grid-area: links;
  grid-template-rows: repeat(5, max-content);

  li {
    align-items: center;
    z-index: 3;
    color: var(--content);
    display: flex;
    gap: 0.5rem;

    a {
      display: flex;
      color: var(--content);
      gap: 0.5rem;
      transition: color 0.15s ease-out;

      &:hover {
        color: var(--primary);
      }
    }
  }
}

@media (min-width: 800px) {
  @media (prefers-reduced-motion: no-preference) {
    .hover-wrapper {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      grid-template-rows: repeat(3, 1fr);
      inset: 0;
      position: absolute;
      z-index: 2;
    }

    article:has(.top-left:hover) {
      transform: rotateX(5deg) rotateY(-5deg);
    }

    article:has(.top-center:hover) {
      transform: rotateX(5deg) rotateY(0deg);
    }

    article:has(.middle-left:hover) {
      transform: rotateX(0deg) rotateY(-5deg);
    }

    article:has(.middle-center:hover) {
      transform: rotateX(0deg) rotateY(0deg);
    }

    article:has(.middle-right:hover) {
      transform: rotateX(0deg) rotateY(5deg);
    }

    article:has(.bottom-left:hover) {
      transform: rotateX(-5deg) rotateY(-5deg);
    }

    article:has(.bottom-center:hover) {
      transform: rotateX(-5deg) rotateY(0deg);
    }

    article:has(.bottom-right:hover) {
      transform: rotateX(-5deg) rotateY(5deg);
    }
  }
}
</style>
