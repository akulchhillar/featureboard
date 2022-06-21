<template>
  <li :class="props.class">
    <a :class="props.class" @click="sendTag"> {{ props.title }} </a>
  </li>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

const emit = defineEmits(["tag-Update"]);

const props = defineProps({
  title: { type: String },
  class: { type: String },
});

const sendTag = () => {
  emit("tag-Update", [props.title, props.class]);
};
</script>

<script>
export default {
  name: "Tag",
};
</script>
