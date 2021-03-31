<template>
  <a :href="slug" :class="customClass">
    {{ name }}
  </a>
</template>

<script>
export default {
  name: "Button",
  props: {
    name: String,
    slug: String,
    customClass: String,
  },
};
</script>
