<template>
  <!--            eslint-disable-next-line-->
  <label class="form__label">
    <!--            eslint-disable-next-line-->
    <slot />
    <span class="form__value">{{ title }}</span>
    <span class="form__error" v-if="error">{{ error }}</span>
  </label>
</template>

<script>
export default {
  props: ['title', 'error'],
};
</script>
