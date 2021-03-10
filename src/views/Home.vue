<template>
  <perfect-scrollbar :class="home">
    <!-- <div class="home">Hello World</div> -->
    <section class="section-1">
      <div class="initials"></div>
      <div class="preface">
        <span class="h4">What we do</span>
        <p class="h1">
          We transform ideas into digital outcomes to elevate the connection between our clients and
          their customers.
        </p>
      </div>
    </section>
    <section class="services__section section-2">
      <div class="vid">
        <video
          src="@/assets/vid/digital-product-and-services_10.mp4"
          class="vid"
          autoplay
          loop
          muted
        ></video>
      </div>
      <div class="description">
        <div class="description__title h3">Digital Products</div>
        <div class="description__body">
          <p class="h4-alt">
            Digital Products are the apps, tools, sites, systems --the list is long-- that you use
            to watch,buy, create, control and manage stuff digitally. Through thorough research and
            after looking into every nook and crany, we create functional, intuitive, engaging, and
            -- let's just say it -- stunning digital products. Why? To meet our client'ss objectives
            providing results and making the world a better place for their users.
          </p>
        </div>
      </div>
    </section>
    <section class="services__section section-3">
      <div class="description">
        <div class="description__title h3">Digital Experiences</div>
        <div class="description__body">
          <p class="h4-alt">
            It’s incredible how these two simple terms can contain a world of feelings. Digital
            experiences are a way of communication that goes beyond language. It’s about the many
            different feelings and interactions that you experience when faced with anything
            digital. It’s about creating a narrative that adds value. It’s about providing results
            to accomplish our client’s needs and make the user tick.
          </p>
        </div>
      </div>
      <div class="vid">
        <video src="@/assets/vid/experience.mp4" class="vid" autoplay loop muted></video>
      </div>
    </section>
    <section class="services__section section-4">
      <div class="vid">
        <video src="@/assets/vid/brand_6.mp4" class="vid" autoplay loop muted></video>
      </div>
      <div class="description">
        <div class="description__title h3">Digital-First Branding</div>
        <div class="description__body">
          <p class="h4-alt">
            Have you ever smelt a perfume and automatically the receptors within your nose rush to
            your brain’s postbox and slip in an image of the person who wore it? Well, that’s
            branding — the faculty of being remembered in many different ways. We just happen to
            make those memories unique and memorable.
          </p>
        </div>
      </div>
    </section>
    <section class="services__section section-5">
      <div class="description">
        <div class="description__title h3">Technology.</div>
        <div class="description__body">
          <p class="h4-alt">
            The base for a successful outcome is also applying the right technological strategy. At
            Plastic, we know about technology. But most importantly, we choose the right technology
            to achieve the expected results you want and, therefore, help you improve. Because if
            misused, technology is as useless as a chocolate fireguard.
          </p>
        </div>
      </div>
      <ul class="tech-stack">
        <li class="h4-alt">- Dev Ops</li>
        <li class="h4-alt">- React</li>
        <li class="h4-alt">- React Native</li>
        <li class="h4-alt">- Vue.js</li>
        <li class="h4-alt">- Node.js</li>
        <li class="h4-alt">- Webflow</li>
        <li class="h4-alt">- Headless CMS</li>
      </ul>
    </section>
    <section class="cta">
      <span class="h4-alt">Got a project?</span>
      <span class="cta__mega h1" @mouseover="fireCtaHover" @mouseleave="removeCtaHover"
        >Let's talk</span
      >
      <i class="cta__icon fa fa-xs fa-arrow-right"></i>
    </section>
    <footer>
      <span class="h5">&copy; 2019 Plastic</span>
      <ul class="footer-links">
        <li class="h5">Privacy Policy</li>
        <li class="h5">Cookies Policy</li>
        <li class="h5">Terms and conditions</li>
      </ul>
    </footer>
  </perfect-scrollbar>
</template>

<script>
// @ is an alias to /src
import anime from 'animejs';

export default {
  name: 'Home',
  components: {},
  methods: {
    fireCtaHover() {
      anime({
        targets: '.cta__icon',
        opacity: 1,
        duration: 250,
        delay: 90,
        translateY: ['80px', 0],
        rotateZ: { value: [0, '30deg', '45deg'], delay: 130 },
        easing: 'easeInOutCirc',
      });
    },
    removeCtaHover() {
      anime({
        targets: '.cta__icon',
        opacity: 0,
        duration: 350,
        delay: 90,
        translateY: [0, '80px'],
        rotateZ: { value: [0], delay: 90 },
        easing: 'easeInOutCirc',
      });
    },
  },
  mounted() {
    this.$nextTick(() => {
      const customCursor = document.getElementById('customCursor');
      const ctaMega = document.querySelector('.cta__mega');

      //  eslint-disable-next-line
      ctaMega.addEventListener('mouseover', function hamburgerHover(e) {
        customCursor.classList.add('cursor--grow-lg');
      });
      //  eslint-disable-next-line
      ctaMega.addEventListener('mouseleave', function hamburgerHover(e) {
        customCursor.classList.remove('cursor--grow-lg');
      });
    });
  },
};
</script>

<style lang="stylus" scoped>
.ps {
  height: 700px;
  height: 100vh;
}

.section-1, .section-2, .section-3, .section-4 .section-5 {
  min-height: clamp(400px, 100vh, 1440px);
  background: #fff;
  text-align: left;
  padding-right: 10em;
  width: 100%;
}

.section-1 {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  padding-left: 20%;

  .initials {
    flex: 1;
  }

  .preface {
    margin: 10vh 0;
    text-align: left;
    // width;
    color: #000;

    span {
      // margin: 200px 0;
    }

    p {
      width: 60%;
      overflow-wrap: break-word;
    }
  }
}

// -----------------------
.services__section {
  display: flex;
  justify-content: space-between;
  // align-items: flex-start;
  margin-top: 5em;

  .vid {
    height: 450px;
    // border: solid 5px yellow;
  }

  .description {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    margin-left: 10em;
    // margin-right: 4em;
    overflow-wrap: break-word;
    text-align: left;

    .description__title {
      margin-bottom: 1.5em;
    }

    .description__body {
    }
  }
}

// --------------------
.section-2 {
  .vid {
    order: 1;
    min-width: 55%;
  }

  .description {
    order: 2;

    .description__title {
    }

    .description__body {
    }
  }
}

.section-3 {
  .vid {
    flex: 1;
    margin-right: 10em;
    // height: 800px;
  }

  .description {
    min-width: 55%;
    padding-right: 10em;
    padding-left: 10em;

    .description__title {
    }

    .description__body {
    }
  }
}

.section-4 {
  .vid {
    margin-left: 5em;
    // height: 800px;
    min-width: calc(55% + 5px);
  }

  .description {
    padding-right: 10em;
    // padding-left: 10em;
    flex: 1;
    justify-content: flex-start;
    // background: crimson;
    margin-left: 0;

    .description__title {
    }

    .description__body {
    }
  }
}

.section-5 {
  min-height: clamp(400px, 100vh, 1440px);
  width: 100%;
  // justify-content: center;
  align-items: center;

  .tech-stack {
    flex: 1;
    display: flex;
    flex-direction: column;
    // padding-left: 0;
    // margin-left: 0;
    // justify-self: flex-start;
  }

  .description {
    // padding-right: 10em;
    padding-left: 10em;
    flex: 1;
    justify-content: flex-start;
    max-width: 40%;

    // background: crimson;
    // margin-left: 0;
    .description__title {
    }

    .description__body {
    }
  }
}

.cta {
  height: clamp(300px, 55vh, 400px);
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  .cta__mega {
    font-size: 7.2rem;
    padding: 0.5em 0;
  }

  .cta__icon {
    font-size: 5.2rem;
    font-weight: 400;
    // margin: 0.3em 0;
    opacity: 0;
  }
}

footer {
  display: flex;
  justify-content: space-around;
  align-items: center;
  min-height: 200px;
  opacity: 0.65;

  .footer-links {
    display: flex;
    justify-self: flex-start;

    & > * {
      padding: 0 0.7em;
    }
  }
}
</style>
