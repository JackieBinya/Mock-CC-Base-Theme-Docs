<template>
  <header class="header" :class="{'header--scrolled' : pageScrolled}">
    <Logo />
    <nav class="nav">
      <MenuToggle v-if="menuToggle" />
    </nav>
  </header>
</template>

<script>

import MenuToggle from '~/components/MenuToggle.vue'
import Logo from '~/components/Logo.vue'
import throttle from 'lodash/throttle'

export default {
  components: {
    MenuToggle,
    Logo
  },
  props: {
    menuToggle: {
      type: Boolean,
      default: true
    }
  },
  data() {
    return {
      pageScrolled: false,
    }
  },
  methods: {
    updateLogo: function() {
      this.logoColor = (this.logoColor == 'dark' ? 'bright' : 'dark')
    },
    headerScroll: function() {
      let fromTop = window.scrollY

      if ((fromTop > 40 && this.pageScrolled == false) || (fromTop <= 40 && this.pageScrolled == true)) {
        this.pageScrolled = !this.pageScrolled
      }
    }
  },
  mounted() {
    window.addEventListener('scroll', this.headerScroll)

    if (process.isClient) {
      this.logoColor = localStorage.getItem('theme')
    }
  }
}
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: fixed;
  top: 0;
  right: -12px;
  left: 0;
  z-index: 10;
  padding: 16px 8px;
  background: $backgroundBright;
  transition: padding .15s linear, background .15s linear, border-color .15s linear;
  will-change: padding, background;
  border-bottom: 1px solid transparent;

  @include respond-above(sm);

  &--scrolled {
    @include respond-below(sm);
  }
}

nav {
  display: flex;
}
</style>

