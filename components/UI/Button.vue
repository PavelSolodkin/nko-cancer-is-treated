<template>
  <button
    :class="['button', className, { button_disabled: disabled }]"
    :disabled="disabled"
    v-on:click="handleClick"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    disabled: Boolean,
    className: String,
  },
  methods: {
    handleClick(e) {
      e.preventDefault();
      if (this.disabled) return;
      this.$emit('btnClick');
    },
  },
};
</script>

<style scoped>
.button {
  width: fit-content;
  min-height: 52px;
  white-space: nowrap;
  padding: 16px 80px;
  border: 0;
  cursor: pointer;
  outline: none;
  color: var(--color-lightgray2);
  font-family: Inter, sans-serif;
  font-weight: 500;
  font-size: 16px;
  background-color: var(--color-purple);
  transition: all 0.3s linear;
}

.button_small {
  padding: 16px 70px;
}

.button:hover {
  opacity: 0.9;
}

.button_disabled {
  opacity: 0.3;
  cursor: default;
}
.button.button_disabled:hover {
  opacity: 0.3;
}

@media screen and (max-width: 1280px) {
  .button {
    min-height: 48px;
  }

  .button_small {
    padding: 15px 45px;
  }
}

@media screen and (max-width: 1024px) {
  .button {
    min-height: 46px;
    font-size: 15px;
  }

  .button_small {
    padding: 14px 49px;
  }
}

@media screen and (max-width: 320px) {
  .button {
    min-height: 40px;
    width: 206px;
    font-size: 13px;
  }

  .button_small {
    padding: 11px 50px;
  }
}
</style>
