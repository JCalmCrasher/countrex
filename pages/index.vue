<template>
  <div
    class="w-2/3 m-auto mt-20 shadow-md rounded-xl bg-white ease-out duration-500 delay-150"
    @keyup="toggleHeightStatus(true, $event)"
    :class="searchBarHeight"
    v-on-clickaway="away"
  >
    <div class="relative text-gray-600">
      <span class="absolute inset-y-0 left-0 flex items-center pl-2">
        <button type="submit" class="p-1 outline-none">
          <svg
            fill="none"
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            viewBox="0 0 24 24"
            class="w-6 h-6"
          >
            <path d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path>
          </svg>
        </button>
      </span>
      <input
        type="search"
        class="w-full h-12 pl-20 outline-none bg-white text-lg"
        placeholder="What country would you like to know about?"
        autocomplete="off"
      />
    </div>
    <hr />
    <div class="relative rounded-md p-3 m-3 cursor-pointer bg-gray-100">
      <span class="text-white bg-blue-700 rounded-md p-2 text-xs"
        ><b>Name:</b> Nigeria</span
      >
      <span class="text-white bg-orange-400 rounded-md p-2 text-xs"
        ><b>Population:</b> 1,000,000</span
      >
      <span class="text-white bg-yellow-700 rounded-md p-2 text-xs"
        ><b>Capital:</b> Abuja</span
      >
      <span class="text-white bg-green-700 rounded-md p-2 text-xs"
        ><b>Region:</b> Africa</span
      >
    </div>
  </div>
</template>

<script>
import { directive as onClickaway } from "vue-clickaway";
export default {
  directives: {
    onClickaway: onClickaway,
  },
  data() {
    return {
      isTouched: false,
      fullContainerHeight: "h-64",
    };
  },
  methods: {
    toggleHeightStatus(param, evt = null) {
      if (evt.target.value.length < 1) {
        this.isTouched = false;
        return;
      }
      this.isTouched = param;
    },
    away: function () {
      this.toggleHeightStatus(false);
    },
  },
  computed: {
    searchBarHeight: function () {
      return {
        "h-64": this.isTouched,
        "h-12": !this.isTouched,
      };
    },
  },
};
</script>