<template>
  <div class="nav-menu">
    <ul class="navlinks__main">
      <NavItem name="Work." ordinal="01" />
      <NavItem name="About." ordinal="02" />
      <NavItem name="Manifesto." ordinal="03" />
      <NavItem name="Contact." ordinal="04" />
    </ul>
    <ul class="navlinks__sub">
      <span class="socials-item h5">Behance</span>
      <span class="socials-item h5">Dribbble</span>
      <span class="socials-item h5">Instagram</span>
      <span class="socials-item h5">LInkedIn</span>
      <span class="socials-item h5">Medium</span>
      <span class="socials-item h5">Twitter</span>
    </ul>
  </div>
</template>

<script>
import NavItem from '@/components/NavItem.vue';

export default {
  components: {
    NavItem,
  },
  methods: {
    fireNavlinkHoverEvent() {},
    removeNavlinkHoverEvent() {},
  },
  mounted() {
    const customCursor = document.getElementById('customCursor');
    const navSelector = document.querySelectorAll('.nav-item');
    const socialsSelector = document.querySelectorAll('.socials-item');

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
  padding: 0vh 8%;

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
      padding: 0.8em 0;
      opacity: 0;
    }
  }
}
</style>
