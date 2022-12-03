<template>
  <div class="inline-block">
    <div
      ref="refrenceRef"
      class="inline-block"
      @mouseenter="show"
      @mouseleave="hide"
      @focus="show"
      @blur="hide"
    >
      <slot />
    </div>
    <div
      ref="floatingRef"
      :class="[
        'absolute top-0 left-0 z-50 bg-gray-600 text-sm text-white px-3 py-1.5 rounded-md cursor-default',
        isHidden && 'hidden',
      ]"
    >
      {{ props.content }}
      <div
        ref="arrowRef"
        class="absolute bg-gray-600 w-[8px] h-[8px] rotate-45"
      ></div>
    </div>
  </div>
</template>

<script setup>
// export default {
//   name: "ToolTip2",
// };

import { computePosition, shift, flip, offset, arrow } from "@floating-ui/dom";
import { ref, defineProps } from "vue";

const props = defineProps({
  content: {
    type: String,
    default: "tooltip",
  },
  placement: {
    type: String,
    default: "bottom",
  },
});

const refrenceRef = ref();
const floatingRef = ref();
const arrowRef = ref();
const isHidden = ref(true);

async function calculatePosition() {
  const { x, y, middlewareData, placement } = await computePosition(
    refrenceRef.value,
    floatingRef.value,
    {
      placement: props.placement,
      middleware: [
        offset(8),
        flip(),
        shift({ padding: 5 }),
        arrow({ element: arrowRef.value }),
      ],
    }
  );

  Object.assign(floatingRef.value.style, {
    left: `${x}px`,
    top: `${y}px`,
  });

  const { x: arrowX, y: arrowY } = middlewareData.arrow;

  const opposedSide = {
    left: "right",
    right: "left",
    bottom: "top",
    top: "bottom",
  }[placement.split("-")[0]];

  Object.assign(arrowRef.value.style, {
    left: arrowX ? `${arrowX}` : "",
    top: arrowY ? `${arrowY}px` : "",
    bottom: "",
    right: "",
    [opposedSide]: "-4px",
  });
}

function hide() {
  isHidden.value = true;
}
function show() {
  isHidden.value = false;
  calculatePosition();
}
</script>

<style></style>
