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
    <section class="section-2"></section>
    <section class="section-3"></section>
    <section class="section-4"></section>
  </perfect-scrollbar>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {},
};
</script>

<style lang="stylus" scoped>
.ps {
  height: 700px;
  background: crimson;
  height: 100vh;
}

.section-1, .section-2, .section-3, .section-4 {
  min-height: 100vh;
  background: #fff;
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
</style>
