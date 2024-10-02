<template>
  <div
    class="bg-black h-screen m-auto flex justify-center items-center main-image"
  >
    <LinkContainer />
  </div>
</template>

<script setup>
import LinkContainer from "./components/LinkContainer";
</script>

<style>
.main-image {
  background: url("./assets/images/beautiful-night-sky-with-shiny-stars.jpg")
    fixed no-repeat;
  background-size: cover;
}
</style>
