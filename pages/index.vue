<template>
  <div>
    <Header />

    <section
      id="main"
      class="h-screen flex flex-row items-center px-5 sm:px-40"
    >
      <div class="grid grid-cols-3 w-full h-50vh">
        <div class="col-span-2 pt-8 rounded-lg mr-2 text-white">
          <div class="text-6xl">TopSoft</div>
          <div class="text-2xl">full range of development services</div>
        </div>
        <div class="bg-tyellow px-6 rounded-lg shadow-2xl flex items-center">
          <LogoDisassemble class="mx-auto"></LogoDisassemble>
        </div>
      </div>
    </section>

    <section data-aos="fade-up" data-aos-delay="100">
      <WhoWeAre />
    </section>

    <section>
      <Services />
    </section>

    <section>
      <div class="h-full">
        <h3 class="text-4xl text-center py-5">CLIENT SUCCESS</h3>
        <div class="flex flex-col">
          <div v-for="project of projects" :key="project.slug">
            <div
              class="my-4 mx-3 sm:mx-auto sm:grid grid-cols-2 sm:w-10/12"
              style="grid-auto-flow: dense"
            >
              <div class="col-span-1 overflow-hidden">
                <!-- :src="require(`~/assets/resources/${project.img}`)" -->
                <img
                  src="https://images.unsplash.com/photo-1615130378909-21b80a796749?crop=entropy&cs=tinysrgb&fit=crop&fm=jpg&h=600&ixlib=rb-1.2.1&q=80&w=600"
                  :alt="project.img"
                  class="
                    transition
                    duration-500
                    ease-in-out
                    transform
                    hover:-translate-y-1
                    hover:scale-110
                    h-full
                    w-full
                    object-cover
                  "
                />
              </div>
              <div
                class="pt-10 pl-3 sm:pl-10 sm:pr-5 col-span-1 sm:h-full"
                style="background-color: #f2eae2"
              >
                <nuxt-link
                  :to="{ name: 'posts-slug', params: { slug: project.slug } }"
                >
                  <div class="flex flex-col">
                    <h2
                      class="font-bold uppercase"
                      style="color: #3098f2; letter-spacing: 0.01em"
                    >
                      {{ project.client }}
                    </h2>
                    <p
                      class="
                        mt-5
                        overflow-ellipsis overflow-hidden
                        font-normal
                        text-3xl
                      "
                      style="height: 45%"
                    >
                      {{ project.description.substring(0, 100) }}
                    </p>
                    <div class="mt-10 flex flex-row">
                      <svg
                        width="24"
                        height="25"
                        viewBox="0 0 24 25"
                        fill="none"
                      >
                        <g>
                          <circle
                            cx="12"
                            cy="12.5"
                            r="12"
                            fill="#3098F3"
                          ></circle>
                          <path
                            d="M10 8L14.5 12.5L10 17"
                            stroke="white"
                            stroke-width="2"
                            stroke-miterlimit="10"
                          ></path>
                        </g>
                        <defs>
                          <clipPath>
                            <rect
                              y="0.5"
                              width="24"
                              height="24"
                              fill="white"
                            ></rect>
                          </clipPath>
                        </defs>
                      </svg>
                      <span class="ml-3 mb-5 font-medium"
                        >View Project Summary</span
                      >
                    </div>
                  </div>
                </nuxt-link>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- <no-ssr>
      <vue-particles
        color="#140957"
        :particleOpacity="0.7"
        :particlesNumber="80"
        shapeType="circle"
        :particleSize="4"
        linesColor="#1EC2F2"
        :linesWidth="1"
        :lineLinked="true"
        :lineOpacity="0.4"
        :linesDistance="150"
        :moveSpeed="3"
        :hoverEffect="true"
        hoverMode="grab"
        :clickEffect="true"
        clickMode="push"
      >
      </vue-particles>
    </no-ssr> -->
  </div>
</template>

<script>
import WhoWeAre from "~/components/WhoWeAre.vue";
export default {
  components: { WhoWeAre },
  updated() {
    document.querySelector(".vhl-navigation")?.remove();
  },
  mounted() {
    document.querySelector(".vhl-navigation")?.remove();

    setInterval(() => {
      if (parseInt(this.progress) === 1) {
        this.progress = 0.1;
        return;
      }
      this.progress = parseFloat((this.progress + 0.1).toFixed(2));
    }, 300);

    // VANTA.TOPOLOGY({
    //   el: "#main",
    //   mouseControls: true,
    //   touchControls: true,
    //   gyroControls: false,
    //   minHeight: 200.0,
    //   minWidth: 200.0,
    //   scale: 1.0,
    //   scaleMobile: 1.0,
    //   color: 0xffffff,
    //   backgroundColor: 0xffd02f,
    // });
  },
  data() {
    return {
      projects: [
        {
          slug: "/1",
          img: "",
          client: "ID Bank",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor",
        },
        {
          slug: "/2",
          img: "",
          client: "ID Bank",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor",
        },
      ],
    };
  },
};
</script>

<style>
.bg-tops-blue {
  background-color: #1ec2f2;
}

.bg-tops-green {
  background-color: #024442;
}

.h-50vh {
  height: 50vh;
}

.h-75vh {
  height: 75vh;
}

.bg-tyellow {
  background-color: #faca30;
}

section {
  padding-top: 5rem;
}

#main {
  background: url("~assets/main.jpg");
  background-repeat: no-repeat;
  background-size: 100% 100%;
  background-size: cover;
}
</style>
