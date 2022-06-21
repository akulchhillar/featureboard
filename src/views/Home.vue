<template>
  <div id="main" class="bg-white">
    <div id="header" class="fixed h-32 w-full top-0 left-0 z-40">
      <NavigationBar />
      <Heading />
    </div>

    <div
      id="content"
      class="mt-40 grid grid-rows-1 grid-cols-3 content-center justify-center z-30"
    >
      <div class="col-start-2">
        <Content />
      </div>
    </div>

    <div
      id="bottom"
      class="grid grid-rows-1 grid-cols-4 bg-white fixed bottom-0 left-0 w-full"
    >
      <div class="col-start-2 col-span-2 mb-5 shadow-lg">
        <BottomInput />
      </div>
    </div>
  </div>
</template>

<script setup>
import NavigationBar from "../components/Navigation.vue";
import Heading from "../components/Heading.vue";
import Content from "../components/Content.vue";
import BottomInput from "../components/BottomInput.vue";
</script>
