<template>
  <div>
    <div class="text-4xl text-center py-5">WHO WE ARE</div>
    <div class="text-lg px-2 sm:px-56 text-center" style="color: #a4a4a4">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
      tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
      veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
      commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
      velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat
      cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id
      est laborum.
    </div>

    <div class="grid grid-cols-4 justify-items-center items-center px-2 sm:px-32 mt-10">
      <img
        v-for="(partner, i) in partners"
        :key="i"
        :src="partner.src"
        class="tb-logo w-1/2"
        style="max-width: 120px;"
      />
    </div>
  </div>
</template>

<script>
const svgImages = require.context("../assets/partners/", true, /\.svg$/);
const pngImages = require.context("../assets/partners/", true, /\.png$/);

let imagesArray = [
  ...Array.from(svgImages.keys()),
  ...Array.from(pngImages.keys()),
];

function constructItems(fileNames) {
  let constructed = [];
  fileNames.forEach((fileName) => {
    constructed.push({
      src: "/_nuxt/assets/partners/" + fileName.substr(1),
    });
  });
  return constructed;
}
let res = constructItems(imagesArray);

export default {
  data: function () {
    return {
      partners: res,
    };
  },
};
</script>

<style>
.tb-logo {
  filter: grayscale(100%);
}

.tb-logo:hover {
  filter: grayscale(0%);
}
</style>