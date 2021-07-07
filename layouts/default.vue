<template>
  <div>
    <Nuxt />
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@100;200;300;400;500;600;700;800;900&display=swap');

html,
body {
  height: 100%;
  font-family: Montserrat, Arial, sans-serif;
}

body {
  background-color: #fff;
  overflow: overlay;
}
a {
  text-decoration: none;
}
/* total width */
body::-webkit-scrollbar {
  background-color: transparent;
}

::-webkit-scrollbar-thumb {
  box-shadow: inset 0 0 10px 10px rgba(128, 128, 128, 0.4);
  border-radius: 16px;
  border: solid 5px transparent;
}
</style>
