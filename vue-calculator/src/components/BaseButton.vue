<template>
  <button
    type="button"
    @click="$emit('click')"
    class="BaseButton"
    :class="classes"
    :disabled="disabled || loading"
  >
    <span v-if="loading">...読み込み中</span><slot v-else></slot>
  </button>
</template>

<script>
export default {
  name: "BaseButton",
  props: {
    type: {
      type: String,
      default: "default",
      validator(val) {
        return [
          "defualt",
          "primary",
          "success",
          "info",
          "warning",
          "danger",
        ].includes(val);
      },
    },
    size: {
      type: String,
      default: "middle",
      validator(val) {
        return ["small", "middle", "large"].includes(val);
      },
    },
    loding: {
      type: Boolean,
      default: false,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    classes() {
      return [" " + this.type + " " + this.size];
    },
  },
};
</script>

<style scoped>
.BaseButton {
  appearance: none;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  height: 32px;
  padding: 0 16px;
  border: none;
  font-size: 12px;
  cursor: pointer;
}

/* size */
.BaseButton.small {
  height: 24px;
  font-size: 10px;
}
.BaseButton.middle {
  height: 32px;
  font-size: 12px;
}
.BaseButton.large {
  height: 40px;
  font-size: 14px;
}

/* type */
.BaseButton.default {
  background-color: gray;
  color: black;
}
.BaseButton.primary {
  background-color: skyblue;
  color: white;
}
.BaseButton.success {
  background-color: lightgreen;
  color: white;
}
.BaseButton.info {
  background-color: yellow;
  color: white;
}
.BaseButton.warning {
  background-color: orange;
  color: white;
}
.BaseButton.danger {
  background-color: red;
  color: white;
}
</style>
