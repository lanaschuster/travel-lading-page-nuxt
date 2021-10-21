<template>
  <main class="main">
    <div class="swiper top">
      <div class="swiper-wrapper">
        <section class="islands swiper-slide">
          <img
            src="/img/pexels-rodolfo-clix.jpg"
            alt="Cataratas do Iguaçu - Imagem de Rodolfo Clix"
            class="islands__bg"
          />
          <div class="islands__container bd-container">
            <div class="islands__data">
              <h2 class="islands__subtitle">Foz do Iguaçu</h2>
              <h1 class="islands__title">Cataratas do Iguaçu</h1>
              <p class="islands__description">
                Small South Pacific island northwest of Tahiti in French
                Polynesia, surrounded by motus.
              </p>
              <a href="#" class="islands__button">
                Explore
                <i class="bx bx-right-arrow-alt islands__button-icon"></i>
              </a>
            </div>
            <div class="islands__video">
              <div class="islands__video-content" @click="popUp">
                <i class="bx bx-play-circle islands__video-icon"></i>
              </div>
            </div>
          </div>
        </section>

        <section class="islands swiper-slide">
          <img src="/img/itaipu.jpg" alt="" class="islands__bg" />
          <div class="islands__container bd-container">
            <div class="islands__data">
              <h2 class="islands__subtitle">Foz do Iguaçu</h2>
              <h1 class="islands__title">Itaipu Binacional</h1>
              <p class="islands__description">
                It is an Indonesian island known and beautiful for its lush
                active volcanic mountains.
              </p>
              <a href="#" class="islands__button"
                >Explore
                <i class="bx bx-right-arrow-alt islands__button-icon"></i
              ></a>
            </div>
            <div class="islands__video">
              <div class="islands__video-content" @click="popUp">
                <i class="bx bx-play-circle islands__video-icon"></i>
              </div>
            </div>
          </div>
        </section>

        <section class="islands swiper-slide">
          <img src="/img/marco-das-tres-fronteiras2.jpg" alt="" class="islands__bg" />
          <div class="islands__container bd-container">
            <div class="islands__data">
              <h2 class="islands__subtitle">Foz do Iguaçu</h2>
              <h1 class="islands__title">Tríplice Fronteira</h1>
              <p class="islands__description">
                Also known as La Paragua, it is the largest island in the
                province of Palawan.
              </p>
              <a href="#" class="islands__button"
                >Explore
                <i class="bx bx-right-arrow-alt islands__button-icon"></i
              ></a>
            </div>
            <div class="islands__video">
              <div class="islands__video-content" @click="popUp">
                <i class="bx bx-play-circle islands__video-icon"></i>
              </div>
            </div>
          </div>
        </section>

        <div id="popup" ref="popup" class="islands__popup">
          <div>
            <div
              id="popup-close"
              class="islands__popup-close"
              @click="closePopUp"
            >
              <i class="bx bx-x"></i>
            </div>
            <iframe
              class="islands__popup-video"
              src="https://www.youtube.com/embed/6GBVaHH_6bQ"
              title="YouTube video player"
              frameborder="0"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
              allowfullscreen
            ></iframe>
          </div>
        </div>
      </div>
    </div>

    <div class="controls thumbs">
      <div class="controls__container swiper-wrapper">
        <img
          class="controls__img swiper-slide"
          src="/img/pexels-rodolfo-clix.jpg"
          alt="Cataratas do Iguaçu"
          @click="scrollAnimation"
        />
        <img
          class="controls__img swiper-slide"
          src="/img/itaipu.jpg"
          alt="Bali"
          @click="scrollAnimation"
        />
        <img
          class="controls__img swiper-slide"
          src="/img/marco-das-tres-fronteiras2.jpg"
          alt="Palawan"
          @click="scrollAnimation"
        />
      </div>
    </div>
  </main>
</template>

<script>
import Swiper from '@/assets/js/swiper-bundle.min.js'
import gsap from '@/assets/js/gsap.min.js'

export default {
  data() {
    return {
      swiper: null,
      thumbs: {},
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
    popUp() {
      const modal = this.$refs.popup
      modal.classList.add('show-popup')
    },
    closePopUp() {
      const modal = this.$refs.popup
      modal.classList.remove('show-popup')
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

      this.closePopUp()
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
.islands__popup {
  display: none;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  background-color: var(--first-color-lighter);
  padding: 1rem 0.75rem;
  border-radius: 1rem;
}
.islands__popup-close {
  position: absolute;
  top: -0.75rem;
  right: -0.75rem;
  display: inline-flex;
  padding: 0.35rem;
  background-color: var(--first-color);
  color: var(--first-color-lighter);
  font-size: 1.2rem;
  border-radius: 50%;
  cursor: pointer;
}
.show-popup {
  display: block;
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