<template>
  <input type="checkbox" :id="props.id" class="modal-toggle" />
  <div class="modal">
    <div class="modal-box">
      <p class="py-4 text-base font-medium">
        Are you sure you want to delete <b>{{ props.featuretitle }} </b> ?
      </p>
      <div class="grid grid-rows-1 grid-cols-6">
        <label
          :for="props.id"
          class="btn btn-active btn-ghost col-start-2 min-w-max max-w-max"
          >No, Don't
        </label>
        <button
          class="btn btn-active col-start-5 min-w-max max-w-max bg-red-300 hover:bg-red-300 hover:text-black text-black border-none"
        >
          Yes, Delete
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
const props = defineProps({
  id: { type: String },
  featuretitle: { type: String },
});
</script>

<script>
export default {
  name: "DeleteModal",
};
</script>
