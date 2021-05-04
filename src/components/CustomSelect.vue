<template>
    <label v-if="label">{{ label }}</label>
    <select
     :value="modelValue"
     v-bind="{
         ...$attrs,
         onChange
     }">
      <option value="">-- Please select --</option>
      <option v-for="option in options"
      :value="option.value"
      :key="option.value"
      :selected="option.value === modelValue">{{ option.text }}</option>
     </select>
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
      default: ''
    },
    options: {
      type: Array,
      required: true
    }
  },
  setup (props, { emit }) {
    const onChange = ($event) => {
      emit('update:modelValue', $event.target.value)
    }
    return { onChange }
  }
}
</script>

<style scoped>

</style>
