<template>
    <input type="radio"
        :checked="modelValue === value"
        :value="value"
        @change="radioChanged"
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
      type: [String, Number],
      default: '' // Empty by default because we do not want preselections.
    },
    value: {
      type: [String, Number],
      required: true
    }
  },
  setup (props, { emit }) {
    const radioChanged = ($event) => {
      emit('update:modelValue', props.value)
    }
    return { radioChanged }
  }
}
</script>

<style lang="scss" scoped>

</style>
