<template>
  <tool-tip content="my tooltip" placement="bottom">
    <button
      class="bg-blue-500 text-white text-sm font-medium rounded-md leading-none px-3 py-2"
    >
      click me
    </button>
  </tool-tip>
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
