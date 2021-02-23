<template>
  <div class="hamburger" id="hamburger" :style="cssVars">
    <div class="bar"></div>
    <div class="bar2"></div>
  </div>
</template>

<script>
export default {
  props: ['navMenu'],
  computed: {
    cssVars() {
      const value = this.navMenu;
      console.log(value);
      if (this.navMenu === true) {
        return {
          '--hamburger-background': '#fff',
        };
      }
      return {
        '--hamburger-background': '#000',
      };
    },
  },
};
</script>

<style lang="stylus" scoped>
.hamburger {
  z-index: 10;
  position: absolute;
  right: 4%;
  top: 4%;
  width: 1em;
  display: flex;
  flex-direction: column;
  padding: 1em 2vw 1em 1vw;

  & > * {
    --hamburger-backgrounds: yellow;
    background: #000;
    background: var(--hamburger-background);
    mix-blend-mode: difference;
    height: 0.2rem;
  }

  .bar {
    width: 1.6rem;
  }

  .bar2 {
    width: 1rem;
    margin-top: 0.2em;
    // transform: translateX(-50%);
  }
}
</style>
