<template>
  <div class="nav-menu">
    <div
      class="showreel h4"
      @mouseenter="fireShowreelHoverEvent"
      @mouseleave="fireShowreelExitEvent"
    >
      Our Showreel
      <div class="showreel-divider"></div>
    </div>
    <ul class="navlinks__main">
      <NavItem name="Work." ordinal="01" />
      <NavItem name="About." ordinal="02" />
      <NavItem name="Manifesto." ordinal="03" />
      <NavItem name="Contact." ordinal="04" />
    </ul>
    <ul class="navlinks__sub">
      <span class="socials-item h4">Behance</span>
      <span class="socials-item h4">Dribbble</span>
      <span class="socials-item h4">Instagram</span>
      <span class="socials-item h4">LInkedIn</span>
      <span class="socials-item h4">Medium</span>
      <span class="socials-item h4">Twitter</span>
    </ul>
  </div>
</template>

<script>
import NavItem from '@/components/NavItem.vue';
import anime from 'animejs';

export default {
  components: {
    NavItem,
  },
  methods: {
    fireNavlinkHoverEvent() {},
    removeNavlinkHoverEvent() {},
    fireShowreelHoverEvent() {
      anime({
        targets: '.showreel-divider',
        width: '99%',
        easing: 'spring(1, 100, 9, 0)',
        delay: 0,
      });
    },
    fireShowreelExitEvent() {
      anime({
        targets: '.showreel-divider',
        width: '15%',
      });
    },
  },
  mounted() {
    const customCursor = document.getElementById('customCursor');
    const navSelector = document.querySelectorAll('.nav-item');
    const socialsSelector = document.querySelectorAll('.socials-item');
    const showreelSelector = document.querySelector('.showreel');

    //  Select nav list
    //  eslint-disable-next-line
    Array.from(navSelector).forEach((item) => {
      item.addEventListener('mouseover', () => {
        customCursor.classList.add('cursor--grow');
      });

      item.addEventListener('mouseleave', () => {
        customCursor.classList.remove('cursor--grow');
      });
    });

    // Select socials
    Array.from(socialsSelector).forEach((item) => {
      item.addEventListener('mouseover', () => {
        customCursor.classList.add('cursor--grow-mid');
      });

      item.addEventListener('mouseleave', () => {
        customCursor.classList.remove('cursor--grow-mid');
      });
    });

    // Select showreel
    showreelSelector.addEventListener('mouseover', () => {
      customCursor.classList.add('cursor--grow-mid');
    });
    showreelSelector.addEventListener('mouseleave', () => {
      customCursor.classList.remove('cursor--grow-mid');
    });
  },
};
</script>

<style lang="stylus" scoped>
.nav-menu {
  z-index: 5;
  position: relative;
  width: 100%;
  height: 100vh;
  background: #000;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  padding: 0vh 0%;

  .navlinks__main {
    color: white;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    position: relative;
  }

  .navlinks__sub {
    color: white;
    display: flex;
    flex-direction: column;
    align-items: flex-start;

    // border: solid thin yellow;

    // height: auto;
    .socials-item {
      margin: 0.8em 0;
      opacity: 0;
    }
  }

  .showreel, .showreel-divider {
    position: absolute;
  }

  .showreel {
    left: 5%;
    bottom: 5%;
    color: #fff;
  }

  .showreel-divider {
    bottom: -0.2em;
    width: 2.2rem;
    height: 0.2rem;
    background: #fff;
  }
}
</style>
