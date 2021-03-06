<template>
  <main class="main">
    <div class="swiper top">
      <div class="swiper-wrapper">
        <section 
          v-for="(item, i) in items"
          :key="`destino_${i}`"
          class="islands swiper-slide"
        >
          <img
            :src="item.imagem"
            :alt="item.alt"
            class="islands__bg"
          />
          <div class="islands__container bd-container">
            <div class="islands__data">
              <h2 class="islands__subtitle">{{ item.subtitulo }}</h2>
              <h1 class="islands__title">{{ item.titulo }}</h1>
              <p class="islands__description">
                {{ item.descricao }}
              </p>
              <a :href="item.link" target="_blank" class="islands__button">
                Explore
                <i class="bx bx-right-arrow-alt islands__button-icon"></i>
              </a>
            </div>
            <div class="islands__video">
              <div class="islands__video-content" @click="popUp(item.videoUrl)">
                <i class="bx bx-play-circle islands__video-icon"></i>
              </div>
            </div>
          </div>
        </section>
      </div>
    </div>

    <div class="controls thumbs">
      <div class="controls__container swiper-wrapper">
        <img
          v-for="(item, i) in items"
          :key="`thumb_${i}`"
          class="controls__img swiper-slide"
          :src="item.imagem"
          :alt="item.alt"
          @click="scrollAnimation"
        />
      </div>
    </div>
    <VideoPopUp :videoUrl="videoUrl" @close="videoUrl = ''" />
  </main>
</template>

<script>
import VideoPopUp from './VideoPopUp.vue'
import Swiper from '@/assets/js/swiper-bundle.min.js'
import gsap from '@/assets/js/gsap.min.js'

export default {
  components: {
    VideoPopUp
  },
  data() {
    return {
      swiper: null,
      thumbs: {},
      videoUrl: '',
      items: [
        {
          subtitulo: 'Foz do Iguaçu',
          titulo: 'Cataratas do Iguaçu',
          imagem: '/img/pexels-rodolfo-clix.jpg',
          alt: 'Cataratas do Iguaçu - Imagem de Rodolfo Clix',
          descricao: 'Conjunto de cerca de 275 quedas de água no rio Iguaçu localizado entre o Brasil e Argentina.',
          videoUrl: 'https://www.youtube.com/embed/mwufrBb90BU',
          link: 'https://cataratasdoiguacu.com.br/'
        },
        {
          subtitulo: 'Foz do Iguaçu',
          titulo: 'Itaipu Binacional',
          imagem: '/img/Itaipu.jpg',
          alt: 'Itaipu Binacional',
          descricao: 'Usina hidrelétrica binacional localizada no Rio Paraná, na fronteira entre o Brasil e o Paraguai. ',
          videoUrl: 'https://www.youtube.com/embed/5Kejx8uZ9pg',
          link: 'https://www.itaipu.gov.br/'
        },
        {
          subtitulo: 'Foz do Iguaçu',
          titulo: 'Parque das Aves',
          imagem: '/img/parque_das_aves.jpg',
          alt: 'Parque das Aves',
          descricao: 'Situado próximo às Cataratas do rio Iguaçu, possui 16 hectares de mata nativa, com 1 500 animais de 140 espécies diferentes, entre aves, répteis e mamíferos.',
          videoUrl: 'https://www.youtube.com/embed/YGoQIvGrRWM',
          link: 'https://www.parquedasaves.com.br/'
        },
        {
          subtitulo: 'Foz do Iguaçu',
          titulo: 'Marco das Três Fronteiras',
          imagem: '/img/marco-das-tres-fronteiras2.jpg',
          alt: 'Marco das Três Fronteiras',
          descricao: 'Onde encontram-se os rios Iguaçu e Paraná, porém mais do que isso, encontram-se três grandes nações da América do Sul: Argentina, Brasil e Paraguai',
          videoUrl: 'https://www.youtube.com/embed/xB_sokYalyQ',
          link: 'https://marcodastresfronteiras.com.br/'
        }
      ]
    }
  },
  mounted() {
    if (!this.swiper) {
      this.thumbs = new Swiper('.thumbs', {
        spaceBetween: 0,
        slidesPerView: 0,
      })
      this.swiper = new Swiper('.top', {
        thumbs: {
          swiper: this.thumbs,
        },
      })
    }
  },
  methods: {
    popUp(videoUrl) {
      this.videoUrl = videoUrl
    },
    scrollAnimation() {
      gsap.from('.islands__subtitle', {
        opacity: 0,
        duration: 0.2,
        delay: 0.2,
        y: -20,
      })

      gsap.from('.islands__title', {
        opacity: 0,
        duration: 0.3,
        delay: 0.3,
        y: -20,
      })

      gsap.from('.islands__description', {
        opacity: 0,
        duration: 0.4,
        delay: 0.4,
        y: -20,
      })

      gsap.from('.islands__button', {
        opacity: 0,
        duration: 0.5,
        delay: 0.5,
        y: -20,
      })

      gsap.from('.islands__video-content', {
        opacity: 0,
        duration: 0.6,
        delay: 0.6,
        y: -20,
      })

      this.videoUrl = ''
    },
  },
}
</script>

<style scoped>
.islands {
  height: 100vh;
  position: relative;
}
.islands__bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  filter: brightness(80%);
  object-fit: cover;
  object-position: center;
}
.islands__container {
  position: relative;
  height: 100%;
  display: grid;
  grid-template-columns: 2fr 0.25fr;
  align-content: center;
}
.islands__subtitle,
.islands__title,
.islands__description {
  color: var(--first-color-lighter);
}
.islands__subtitle {
  font-size: var(--big-font-size);
  font-weight: var(--font-medium);
}
.islands__title {
  font-size: var(--biggest-font-size);
}
.islands__description {
  margin-bottom: 1rem;
}
.islands__button {
  display: inline-flex;
  align-items: center;
  padding: 1rem 1.5rem;
  background-color: var(--first-color-lighter);
  color: var(--first-color);
  border-radius: 0.5rem;
  font-weight: var(--font-medium);
}
.islands__button:hover {
  background-color: var(--body-color);
}
.islands__button:hover .islands__button-icon {
  transform: translateX(0.25rem);
  transition: 0.3s;
}
.islands__button-icon {
  font-size: 1.5rem;
  margin-left: 0.5rem;
}
.islands__video {
  display: flex;
  align-items: flex-end;
  padding-bottom: 0.75rem;
}
.islands__video-content {
  display: inline-flex;
  padding: 0.15rem;
  background-color: var(--first-color-lighter);
  border-radius: 50%;
  cursor: pointer;
}
.islands__video-icon {
  font-size: 1.8rem;
  color: var(--first-color);
}

.controls__img {
  width: 35px;
  height: 35px;
  border-radius: 0.5rem;
  cursor: pointer;
}
.controls {
  position: absolute;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  padding: 0.25rem;
  background-color: var(--first-color-lighter);
  border-radius: 0.75rem;
  overflow: hidden;
  z-index: 200;
}
.controls__container {
  display: flex;
  align-items: center;
  column-gap: 1rem;
}
@media screen and (max-width: 320px) {
  .controls__container {
    column-gap: 0.25rem;
  }
  .islands__popup-video {
    width: 230px;
    height: 100px;
  }
}
@media screen and (min-width: 768px) {
  .islands__container {
    grid-template-columns: repeat(2, 1fr);
  }
  .islands__description {
    padding-right: 5rem;
    margin-bottom: 2rem;
  }
  .islands__video {
    justify-content: center;
    align-items: center;
    padding: 0;
  }
  .islands__video-icon {
    font-size: 3rem;
  }
  .islands__popup-video {
    width: 500px;
    height: 250px;
  }
  .islands__popup-close {
    font-size: 1.5rem;
  }
  .controls {
    padding: 0.5rem;
    border-radius: 1.25rem;
  }
  .controls__container {
    column-gap: 1.5rem;
  }
  .controls__img {
    width: 45px;
    height: 45px;
  }
  .controls__img {
    width: 45px;
    height: 45px;
    border-radius: 0.75rem;
  }
  .swiper-slide-thumb-active {
    width: 55px;
    height: 55px;
  }
}
@media screen and (min-width: 1024px) {
  .islands__description {
    padding-right: 11rem;
  }
}
/* @media screen and (min-width: 721px) {
  .islands{
    height: 640px;
  }
} */
</style>