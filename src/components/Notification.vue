<script setup>
import { ref, computed } from "vue";

const props = defineProps({
  color: {
    type: String,
    required: false,
    validator(value) {
      return [
        "primary",
        "link",
        "info",
        "success",
        "warning",
        "danger",
        "white",
        "light",
        "dark",
        "black",
      ].includes(value);
    },
  },
  light: {
    type: Boolean,
    required: false,
  },
  dark: {
    type: Boolean,
    required: false,
  },
});

const visible = ref(true);

const classNames = computed(() => {
  let names = [];
  if (props.color) {
    names.push("is-" + props.color);
  }
  if (props.light) {
    names.push("is-light");
  }
  if (props.dark) {
    names.push("is-dark");
  }
  return names.join(" ");
});

function close() {
  visible.value = false;
}
</script>

<template>
  <div v-if="visible" class="notification-wrapper">
    <div class="notification" :class="classNames">
      <button class="delete" @click="close"></button>
      <slot> Default notification message. </slot>
    </div>
  </div>
</template>

<style scoped>
.notification-wrapper {
  display: flex;
  justify-content: center;
  margin: 1rem 0;
}

.notification {
  display: inline-block;
  max-width: 600px;
}
</style>
