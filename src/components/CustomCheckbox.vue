<template>
    <input type="checkbox"
        :checked="modelValue"
        @change="checkboxChanged"
        v-bind="$attrs" />
    <label v-if="label">{{ label }}</label>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      default: ''
    },
    modelValue: {
      type: Boolean,
      default: false
    }
  },
  setup (props, { emit }) {
    const checkboxChanged = ($event) => {
      emit('update:modelValue', $event.target.checked)
    }
    return { checkboxChanged }
  }
}

</script>

<style scoped>

</style>
