<template>
  <div class="bg-white">
    <div class="grid grid-rows-1 content-center justify-center bg-white">
      <div>
        <div class="tooltip" data-tip="Click To Edit">
          <h1
            class="text-center text-5xl font-normal outline-none"
            contenteditable="true"
            @keydown="character_check"
          >
            {{ board_name }}
          </h1>
        </div>
      </div>
    </div>
    <div class="mt-2 grid grid-rows-1 grid-cols-3 bg-white">
      <div class="dropdown col-start-2">
        <label tabindex="0">
          <div
            class="text-lg font-medium outline-none btn btn-ghost btn-xs hover:bg-white"
          >
            Sort By
          </div>
        </label>
        <ul
          tabindex="0"
          class="dropdown-content menu p-2 shadow bg-base-100 rounded-box max-w-max"
        >
          <li>
            <label for="" class="active:bg-transparent">
              <a class="text-sm font-medium">Date</a>
            </label>
          </li>
          <li>
            <label for="" class="active:bg-transparent">
              <a class="text-sm font-medium">Upvotes</a>
            </label>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
const board_name = ref("Board Name");
let maxChars = 20;
let currentChars = 0;
const character_check = (event) => {
  currentChars = event.target.textContent.length;
  let keypressed = event.keyCode || event.charCode;
  if (currentChars >= maxChars) {
    if (keypressed != 8) {
      event.preventDefault();
    }
  } else {
    if (keypressed == 13) {
      event.preventDefault();
    }
    currentChars = event.target.textContent.length;
    board_name.value = event.target.textContent;
  }
};
</script>

<script>
import { ref } from "vue";
</script>
