<template>
  <header class="header">
    <nav class="nav bd-container">
      <a href="" class="nav__logo">Travel</a>
      <div id="nav-menu" ref="navMenu" class="nav__menu">
        <ul class="nav__list">
          <li class="nav__item">
            <a href="#" class="nav__link">Home</a>
          </li>
          <li class="nav__item">
            <a href="#" class="nav__link">Explore</a>
          </li>
          <li class="nav__item">
            <a href="#" class="nav__link">Destinations</a>
          </li>
          <li class="nav__item">
            <a href="#" class="nav__link">Hotels</a>
          </li>
        </ul>
      </div>
      <div
        id="nav-toggle"
        ref="navToggle"
        class="nav__toggle"
        @click="showMenu"
      >
        <i class="uil uil-bars"></i>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  methods: {
    showMenu() {
      const nav = this.$refs.navMenu
      if (nav) {
        nav.classList.toggle('show-menu')
      }
    },
  },
}
</script>