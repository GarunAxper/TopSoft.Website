<template>
  <header
    class="fixed top-0 w-full z-50 bg-transparent"
    style="transition: all 0.3s ease 0s"
  >
    <nav>
      <div
        class="flex flex-col sm:flex-row items-center content-center sm:px-40 py-1 font-bold text-lg"
        :class="!useDarkLogo ? 'bg-transparent text-white pt-10' : 'bg-white shadow'"
        style="transition: all 0.3s ease 0s"
      >
        <Logo :useDarkTheme="useDarkLogo" width="6em" class="block" />
        <nuxt-link class="tops-blue text-center p-5 ml-3" to="/">
          Home
        </nuxt-link>
        <nuxt-link class="tops-blue text-center p-5" to="/blog">
          Blog
        </nuxt-link>
        <button class="bg-tops-blue px-4 rounded-tl-2xl rounded-br-2xl h-8 sm:ml-auto text-white">
          Get in touch
        </button>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  data: function () {
    return {
      mobileMenuOpen: true,
      prevScrollpos: 0,
      useDarkLogo: false
    };
  },
  beforeMount() {
    this.mobileMenuOpen = true && window.innerWidth > 640;
  },
  mounted() {
    window.addEventListener("scroll", this.onScroll);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.onScroll);
  },
  methods: {
    onScroll(e) {
      if (this.prevScrollpos === 0) {
        this.prevScrollpos = window.pageYOffset;
      }

      let currentScrollPos = window.pageYOffset;

      if (this.prevScrollpos > currentScrollPos) {
        document.querySelector("header").style.top = "0";
      } else {
        document.querySelector("header").style.top = "-100%";
      }

      this.prevScrollpos = currentScrollPos;
      this.useDarkLogo = currentScrollPos >= 10;
    },
  },
};
</script>

<style>
.tops-blue:hover {
  color: #1ec2f2;
}
</style>
