<template>
  <div class="form-control">
    <div class="input-group">
      <input
        type="text"
        placeholder="Add A New Feature"
        class="input input-bordered border-2 w-full focus:border-none focus:bg-gray-50"
      />
      <button class="btn btn-square">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="24"
          height="24"
          viewBox="0 0 24 24"
          fill="none"
          stroke="#ffffff"
          stroke-width="2"
          stroke-linecap="round"
          stroke-linejoin="round"
        >
          <path d="M3 3h18v18H3zM12 8v8m-4-4h8" />
        </svg>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "BottomInput",
};
</script>
