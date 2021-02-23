<template>
  <div id="app">
    <section>
      <h1>Scroll down</h1>
    </section>
    <section class="dark">
      <div class="content">
        <h2>Who goes there</h2>
        <p>whatya saying?</p>
      </div>
      <img src="../assets/alex.jpg" alt="" />
    </section>
    <section></section>
  </div>
</template>

<script>
import { gsap } from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);
export default {
  mounted() {
    this.$nextTick(() => {
      const tl = gsap.timeline({
        scrollTrigger: {
          trigger: '.dark',
          start: 'center bottom',
        },
      });
      tl.from('img', { x: 200, opacity: 0, duration: 1.5 }).from(
        '.content',
        { y: 300, opacity: 0, duration: 1 },
        '-=1',
      );
    });
  },
};
</script>

<style lang="stylus">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;

  section {
    height: 100vh;
    text-align: center;
  }

  .box {
    background: red;
    width: 200px;
    height: 200px;
  }

  .dark {
    text-align: left;
    background: rgb(27, 27, 27);
    color: #fff;
    position: relative;
  }

  img {
    width: 50%;
    height: 100vh;
    position: absolute;
    object-fit: cover;
    right: 0;
    top: 0;
    z-index: 0;
  }

  .content {
    padding: 9em 5em;
    z-index: 1;
    position: relative;

    h2 {
      font-size: 5em;
      margin-bottom: 0;
    }

    p {
      font-size: 1.6em;
    }
  }
}
</style>
