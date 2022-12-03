<template>
  <div class="flex items-center justify-center mt-16">
    <tool-tip content="my tooltip" placement="top">
      <button
        class="bg-red-500 text-white text-sm font-medium rounded-md leading-none px-3 py-2"
      >
        Top
      </button>
    </tool-tip>
  </div>
  <div class="flex items-center justify-center m-8">
    <tool-tip content="my tooltip" placement="right">
      <button
        class="bg-blue-500 text-white text-sm font-medium rounded-md leading-none px-3 py-2"
      >
        Right
      </button>
    </tool-tip>
  </div>
  <div class="flex items-center justify-center mb-8">
    <tool-tip content="my tooltip" placement="left">
      <button
        class="bg-green-500 text-white text-sm font-medium rounded-md leading-none px-3 py-2"
      >
        Left
      </button>
    </tool-tip>
  </div>
  <div class="flex items-center justify-center mb-8">
    <tool-tip content="my tooltip" placement="bottom">
      <button
        class="bg-pink-500 text-white text-sm font-medium rounded-md leading-none px-3 py-2"
      >
        Bottom
      </button>
    </tool-tip>
  </div>
</template>

<script>
import ToolTip from "@/components/ToolTip.vue";

export default {
  name: "App",
  components: {
    ToolTip,
  },
};
</script>
