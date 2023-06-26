<template>
  <button :disabled="disabled" :type="type" :class="className">
    {{ content }}
  </button>
</template>

<script>
export default {
  props: {
    disabled: {
      type: Boolean,
      default: false,
    },
    type: {
      type: String,
      required: true,
    },
    className: {
      type: String,
      required: true,
    },
    content: {
      type: String,
      required: true,
    },
  },
};
</script>
