<template>
        <input type="radio" v-bind="$attrs" @change="$emit('update:modelValue', $props.value)" :checked="modelValue === value" :value="value" />
        <label v-if="label">{{ label }}</label>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      default: ''
    },
    name: {
      type: String,
      required: true,
      default: ''
    },
    modelValue: {
      type: [String, Number],
      default: ''
    },
    value: {
      type: [String, Number],
      default: ''
    }
  }
}
</script>
