<template>
  <button
    class="button"
    :style="cssProps"
    :class="`button-color--${color}`"
    :disabled="disabled || loading"
    @click="clicked()"
  >
    <div v-if="loading" class="loading-container">
      <loading active button />
    </div>
    <slot v-else>{{ buttonText }}</slot>
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    color: {
      type: String,
      default: 'primary',
      validator(value) {
        return ['primary', 'secondary', 'tertiary'].indexOf(value) !== -1;
      },
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    loading: {
      type: Boolean,
      default: false,
    },
    buttonText: {
      type: String,
      default: 'button',
    },
    width: {
      type: String,
      default: '200px',
    },
  },
  computed: {
    cssProps() {
      return {
        '--width': this.width,
      };
    },
  },
  methods: {
    clicked() {
      this.$emit('click');
    },
  },
};
</script>

<style lang="scss" scoped>
@import '@/assets/styles/colors.scss';

.button {
  width: var(--width);
  border: none;
  padding: 8px 0;
  font-size: 14px;
  border-radius: 12px;
  font-weight: 700;
  font-style: normal;
  line-height: 24px;
  cursor: pointer;
  transition: all 0.3s ease;
}
// Button Primary
.button-color--primary {
  background-color: $primary;
  color: $white;
  &:hover,
  &:active {
    background-color: $pink-100;
    outline: none;
    border: none;
  }
  &:focus {
    outline: none;
  }
  &:disabled {
    cursor: default !important;
    background-color: $pink-300;
    outline: none;
    border: none;
  }
}
// Button Secondary
.button-color--secondary {
  color: $primary;
  background-color: $pink-500;
  &:hover,
  &:active {
    background-color: $pink-400;
    outline: none;
    border: none;
  }
  &:focus {
    outline: none;
  }
  &:disabled {
    cursor: default !important;
    background-color: $pink-500;
    color: $pink-300;
    outline: none;
    border: none;
  }
}
// Button Tertiary
.button-color--tertiary {
  color: $primary;
  background-color: $white;
  &:hover,
  &:active {
    background-color: $pink-500;
    outline: none;
    border: none;
  }
  &:focus {
    outline: none;
  }
  &:disabled {
    cursor: default !important;
    background-color: $white;
    color: $pink-300;
    outline: none;
    border: none;
  }
}
.loading-container {
  height: 24px;
  width: 100%;
}
</style>
