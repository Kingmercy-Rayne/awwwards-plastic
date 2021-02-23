<template>
  <fragment>
    <span class="label" v-show="isHoverActive">{{ ordinal }}</span>
    <div
      class="h2 nav-item"
      :class="{ 'nav-item--active': isHoverActive }"
      @mouseover="isHoverActive = true"
      @mouseleave="isHoverActive = false"
    >
      {{ name }}
    </div>
  </fragment>
</template>

<script>
import { Fragment } from 'vue-fragment';

export default {
  props: {
    name: {
      type: String,
      default: 'NavLink',
    },
    ordinal: {
      type: String,
      default: '01',
    },
  },
  components: { Fragment },
  mounted() {
    //  eslint-disable-next-line
    //  eslint-disable-next-line
  },
  data() {
    return {
      isHoverActive: false,
    };
  },
  computed: {
    cssVars() {
      const value = this.ordinal;
      console.log(value);
      return {
        '--moi': 'purple',
      };
    },
  },
};
</script>

<style lang="stylus" scoped>
.nav-item {
  position: relative;
  padding: 0.1em;
  margin: 1.1em 0;
}

span {
  position: relative;
  font-size: 0.1em;
  left: -3vw;
  transform: translateY(450%);
  transition: all 0.3s cubic-bezier(0.45, -0.19, 0.16, 1.16);
}
</style>
