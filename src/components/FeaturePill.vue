<template>
  <tr class="hover:shadow-md max-w-md min-w-md">
    <td class="rounded-l-lg bg-gray-50">
      <div class="tooltip" data-tip="Upvotes">
        <div class="badge badge-lg">{{ props.upvotes }}</div>
      </div>
    </td>
    <td class="bg-gray-50">
      <div class="flex items-center space-x-3">
        <div>
          <div class="font-normal text-xl text-ellipsis overflow-hidden">
            {{ props.title }}
          </div>
          <div class="text-sm opacity-50">{{ props.createdDate }}</div>
        </div>
      </div>
    </td>

    <td class="bg-gray-50">
      <button class="btn btn-ghost btn-xs" :class="local_class">
        {{ local_tag }}
      </button>
    </td>
    <td class="rounded-r-lg bg-gray-50">
      <div class="dropdown dropdown-end">
        <label tabindex="0" class="btn btn-ghost btn-square">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            class="inline-block w-5 h-5 stroke-current"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M5 12h.01M12 12h.01M19 12h.01M6 12a1 1 0 11-2 0 1 1 0 012 0zm7 0a1 1 0 11-2 0 1 1 0 012 0zm7 0a1 1 0 11-2 0 1 1 0 012 0z"
            ></path>
          </svg>
        </label>
        <ul
          tabindex="0"
          class="menu menu-compact dropdown-content mt-3 p-2 shadow bg-base-100 rounded-box w-52"
        >
          <li>
            <label :for="uuid" class="active:bg-transparent">
              <a>Edit</a>
            </label>
          </li>
          <li class="dropdown">
            <label tabindex="0" class="active:bg-transparent">
              <a>Select A Tag</a>
            </label>
            <ul
              tabindex="0"
              class="menu menu-compact dropdown-content mt-3 p-2 shadow bg-base-100 rounded-box w-52"
            >
              <Tag
                title="New"
                class="bg-emerald-300 hover:bg-emerald-300 hover:text-black"
                @tag-update="receiveTag"
              />
              <Tag
                title="Discussion"
                class="bg-orange-300 hover:bg-orange-300 hover:text-black"
                @tag-update="receiveTag"
              />
              <Tag
                title="In-Progress"
                class="bg-blue-300 hover:bg-blue-300 hover:text-black"
                @tag-update="receiveTag"
              />
              <Tag
                title="Testing"
                class="bg-amber-300 hover:bg-amber-300 hover:text-black"
                @tag-update="receiveTag"
              />
              <Tag
                title="Shipped"
                class="bg-pink-300 hover:bg-pink-300 hover:text-black"
                @tag-update="receiveTag"
              />
            </ul>
          </li>
          <li>
            <label for="" class="active:bg-transparent">
              <a class="bg-transparent">Hide From Board</a></label
            >
          </li>
          <li>
            <label
              :for="delete_uuid"
              class="bg-red-300 hover:bg-red-300 hover:text-black"
            >
              <a class="bg-red-300 hover:bg-red-300 hover:text-black"
                >Delete</a
              ></label
            >
          </li>
        </ul>
      </div>
    </td>
  </tr>
  <EditModal :id="uuid" :featuretitle="props.title" />
  <DeleteModal :id="delete_uuid" :featuretitle="props.title" />
</template>

<script setup>
import { defineProps } from "vue";
import EditModal from "./EditModal.vue";
import DeleteModal from "./DeleteModal.vue";
import Tag from "../components/Tag.vue";

const uuid = crypto.randomUUID();
const delete_uuid = crypto.randomUUID();

const props = defineProps({
  title: { type: String },
  upvotes: { type: Number },
  tag: { type: String },
  createdDate: {
    type: Date,
    default: function () {
      return new Date().toLocaleDateString("en-us", {
        weekday: "long",
        year: "numeric",
        month: "short",
        day: "numeric",
      });
    },
  },
});

const receiveTag = (para) => {
  local_tag.value = para[0];
  local_class.value = para[1];
};

const local_tag = ref(props.tag);
const local_class = ref(null);
</script>

<script>
import { ref } from "vue";
export default {
  name: "FeaturePill",
};
</script>
