<template>
  <input type="checkbox" :id="props.id" class="modal-toggle" />
  <div class="modal">
    <div class="modal-box w-11/12 max-w-5xl h-1/2">
      <h3
        class="rounded font-bold text-lg outline-none focus:bg-gray-50 focus:outline focus:outline-2 focus:outline-slate-400 hover:outline hover:outline-2 hover:outline-gray-400"
        contenteditable="true"
        @keydown="character_check"
      >
        {{ props.featuretitle }}
      </h3>

      <div id="editor" class="my-5 h-2/5">
        <QuillEditor
          theme="snow"
          :toolbar="toolbar"
          placeholder="Give Your Feature A Summary"
        />
      </div>

      <div class="grid grid-rows-1 grid-cols-6 mt-24">
        <label :for="props.id" class="btn btn-active btn-ghost col-start-2"
          >Discard
        </label>
        <button class="btn btn-active col-start-5">Save</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { QuillEditor } from "@vueup/vue-quill";
import "@vueup/vue-quill/dist/vue-quill.snow.css";
import "@vueup/vue-quill/dist/vue-quill.bubble.css";
import { defineProps } from "vue";

let toolbar = [
  [{ size: ["small", false, "large", "huge"] }],
  [{ list: "ordered" }, { list: "bullet" }],
  ["bold", "italic", "underline"],
  ["link"],
  ["blockquote", "code-block"],
  [{ align: [] }],
];

const props = defineProps({
  id: { type: String },
  featuretitle: { type: String },
});
</script>

<script>
let maxChars = 100;
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
  }
};

export default {
  name: "EditModal",
};
</script>
