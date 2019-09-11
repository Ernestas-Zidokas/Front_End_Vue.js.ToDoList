<template>
  <div class="text-field">
    <label v-if="labelText" class="text-field__label" :for="`text_field${_uid}`">{{labelText}}</label>
    <input
      :type="type"
      :value="value"
      @input="handleInput"
      v-bind="attrs"
      :id="`text_field${_uid}`"
      class="text-field__input"
    />
  </div>
</template>

<script>
export default {
  name: "BaseInputField",
  inheritAttrs: false,
  data() {
    return {
      defaults: {
        type: "text"
      }
    };
  },
  methods: {
    handleInput(event) {
      this.$emit("input", event.target.value);
    }
  },
  props: {
    type: {
      type: String,
      default: "text"
    },
    value: {
      type: String,
      default: null
    },
    labelText: {
      type: String,
      default: null
    }
  },
  computed: {
    attrs() {
      return { ...this.defaults, ...this.$attrs };
    }
  }
};
</script>

<style>
</style>