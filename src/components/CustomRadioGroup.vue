<template>
    <component
        v-for="option in options"
        :key="option.value"
        :is="vertical ? 'div' : 'span'"
        :class="{ horizontal: !vertical }">
    <CustomRadio
        :label="option.label"
        :value="option.value"
        :name="name"
        :modelValue="modelValue"
        @update:modelValue="radioGroupChanged" />
    </component>
</template>

<script>
export default {
  props: {
    options: {
      type: Array,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    modelValue: {
      type: [String, Number],
      required: true
    },
    vertical: {
      type: Boolean,
      default: false
    }
  },
  setup (props, { emit }) {
    const radioGroupChanged = ($event) => {
      emit('update:modelValue', $event)
    }

    return { radioGroupChanged }
  }
}
</script>

<style  scoped>
.horizontal {
    margin-right: 1.125rem;
}
</style>
