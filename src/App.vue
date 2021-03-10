<template>
  <div id="app">
    <div class="cursor" id="customCursor" ref="customCursor" :style="cursorVars"></div>
    <span class="logo h3" :style="[!isNavOpen ? { color: '#000' } : { color: '#fff' }]"
      >Plastic.</span
    >
    <Hamburger @click.native="fireAway()" :nav-menu="this.isNavOpen" />
    <transition
      @before-enter="beforeNavEnter"
      @enter="navEnter"
      @leave="navLeave"
      :css="false"
      mode="out-in"
    >
      <NavMenu v-if="isNavOpen" />
    </transition>
    <router-view></router-view>
    <div class="fab">
      <!--eslint-disable-->
      <svg
        width="40px"
        height="40px"
        viewBox="0 0 40 40"
        version="1.1"
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
      >
        <g stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
          <g transform="translate(-48.000000, -960.000000)" fill="#000000" class="fill" style="">
            <path
              d="M68,960 C79.045695,960 88,968.954305 88,980 C88,991.045695 79.045695,1000 68,1000 C56.954305,1000 48,991.045695 48,980 C48,968.954305 56.954305,960 68,960 Z M74,975 L62,975 L62,983 L66,983 L70,986 L70,983 L74,983 L74,975 Z"
            />
          </g>
        </g>
      </svg>
      <!--eslint-enable-->
      <span class="h5-alt">Let's talk</span>
    </div>
  </div>
</template>

<script>
import anime from 'animejs';
import NavMenu from '@/components/NavMenu.vue';
import Hamburger from '@/components/Hamburger.vue';

export default {
  components: {
    NavMenu,
    Hamburger,
  },
  data() {
    return {
      isNavOpen: false,
    };
  },
  computed: {
    // Create computed-style to mitigate specificity issue that arises upon direct style bind
    cursorVars() {
      if (this.isNavOpen) {
        return { '--cursor-bg-color': '#fff' };
      }
      return { '--cursor-bg-color': '#000' };
    },
  },
  methods: {
    fireAway() {
      this.isNavOpen = !this.isNavOpen;
    },
    //  eslint-disable-next-line
    beforeNavEnter(el, done) {
      const tl = anime.timeline();
      tl.add({
        targets: '.nav-menu',
        opacity: 0.2,
      }).add({
        targets: '.navlinks__main',
        translateY: '40%',
      });
    },

    //  eslint-disable-next-line
    navEnter(el, done) {
      const tl = anime.timeline();
      tl.add({
        targets: '.nav-menu',
        // scaleY: [-0.6, 1],
        // translateY: [-200, 0],
        opacity: 1,
        duration: 2000,
        height: '100%',
        easing: 'easeOutElastic(0.9,2)',
        // easing: 'easeInQuart',
      })
        .add(
          {
            targets: '.navlinks__main',
            translateY: [-20, 0],
            duration: 50,
            easing: 'easeInOutQuad',
          },
          300,
        )
        .add(
          {
            targets: '.nav-item',
            opacity: 1,
            translateY: 0,
            duration: 120,
            delay: anime.stagger(150, { easing: 'easeOutQuad' }),
            // delay: 100,
          },
          50,
        )
        .add(
          {
            targets: '.socials-item',
            opacity: 1,
            translateY: 0,
            duration: 40,
            delay: anime.stagger(100, { easing: 'easeOutQuad' }),
            // delay: 100,
          },
          10,
        )
        .add(
          {
            targets: '.hamburger .bar1',
            rotate: 40,
            easing: 'easeInOutSine',
            duration: 200,
          },
          150,
        )
        .add(
          {
            targets: '.hamburger .bar2',
            rotate: 130,
            width: '1.6rem',
            translateY: '0.3em',
            translateX: '-0.3em',
            easing: 'easeInOutSine',
            duration: 200,
          },
          200,
        )
        .add(
          {
            targets: '.showreel',
            opacity: [0, 1],
            translateX: [-10, 0],
            duration: 2000,
          },
          300,
        );

      done();
    },

    //  eslint-disable-next-line
    navLeave(el, done) {
      const tl = anime.timeline();
      tl.add(
        {
          targets: '.nav-menu',
          opacity: 0.4,
          duration: 100,
          // height: 40,
          background: 'yellow',
          // easing: 'easeOutElastic(8,2)',
        },
        10,
      )
        .add({
          targets: '.hamburger .bar1',
          rotate: 0,
          duration: 600,
          complete: done,
        })
        .add(
          {
            targets: '.hamburger .bar2',
            rotate: 0,
            width: '1rem',
            translateY: 0,
            translateX: 0,
            easing: 'easeInOutSine',
            duration: 400,
          },
          10,
        );

      done();
    },
  },
  mounted() {
    this.$nextTick(() => {
      const customCursor = document.getElementById('customCursor');
      const hamburger = document.getElementById('hamburger');

      // change VH varable
      const vh = window.innerHeight * 0.01;
      document.documentElement.style.setProperty('--vh', `${vh}px`);

      // mouse cursor tracking
      //  eslint-disable-next-line
      window.addEventListener('mousemove', function fireCursorEvent(e) {
        customCursor.style.top = `${e.pageY}px`;
        customCursor.style.left = `${e.pageX}px`;
      });

      //  eslint-disable-next-line
      hamburger.addEventListener('mouseover', function hamburgerHover(e) {
        customCursor.classList.add('cursor--grow');
      });
      //  eslint-disable-next-line
      hamburger.addEventListener('mouseleave', function hamburgerHover(e) {
        customCursor.classList.remove('cursor--grow');
      });
    });
  },
};
</script>

<style lang="stylus">
#app {
  position: relative;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000;
  height: 100vh;
  width: 100%;
  font-family: var(--font-family--primary);
  cursor: none;
  overflow: hidden;

  .logo {
    z-index: 10;
    position: absolute;
    top: 4%;
    left: 3%;
    transform: rotate(-180deg);
    // transform: rotate(-90deg);
    // color: #000;
    text-transform: capitalize;
    writing-mode: vertical-rl;
    // transform: translateX(50%);
  }

  .fab {
    position: absolute;
    bottom: 8%;
    left: 3%;
    transform: rotate(-180deg);
    writing-mode: vertical-rl;
    text-transform: capitalize;
    display: flex;
    justify-content: center;
    align-items: center;

    span {
      flex-basis: 70%;
      margin: 1em 0;
    }

    svg {
      // display: none;
      transform: rotate(180deg) scale(1.2);
    }
  }
}

.cursor {
  position: absolute;
  // throw it outta the viewport
  top: -5%;
  z-index: 4000;
  width: 1rem;
  height: 1rem;
  transform: translate(-50%, -50%);
  // border: solid 2px var(--border-color--primary);
  background: #fff;
  background: var(--cursor-bg-color);
  border-radius: 50%;
  pointer-events: none;
  transition: transform, border 0.1ms ease-in;

  @media screen and (max-width: 800px) {
    display: none;
  }
}

.cursor--grow, .cursor--grow-mid, .cursor--grow-lg {
  background: transparent;
  border: none;
  z-index: 20;
  // backdrop-filter: blur(2px);
  backdrop-filter: invert(1.3);
  // transition: all 100ms cubic-bezier(0.45, -0.19, 0.16, 1.16);
  transition: all 100ms ease-in;
}

.cursor--grow {
  transform: scale(4);
}

.cursor--grow-mid {
  transform: scale(2.5);
}

.cursor--grow-lg {
  transform: scale(6);
}

.cursor--hide {
  // visibility: hidden;
  transform: scale(4);
  background: transparent;
  border: none;
  z-index: 20;
  backdrop-filter: grayscale();
  transition: all 220ms ease-in-out;
}
</style>
