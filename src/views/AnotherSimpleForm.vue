<template>
    <div>
        <CustomSelect :options="parishes" v-model="selectedParish" label="Select a letter" class="field" />
        <div>
            <CustomCheckbox label="Is Capital?" v-model="extras.isCapital" class="field" />
        </div>

        <div>
            <CustomCheckbox label="Has Many Towns?" v-model="extras.hasManyTowns" @update:modelValue="handleUpdate" class="field" />
        </div>

        <h3>Attractions</h3>
        <div>
        <CustomRadioGroup
            v-model="attractions"
            name="attractions"
            :options="attractionOptions"
            vertical />
        </div>

        <span>Selected: {{ selectedParish }}</span>

        <pre>{{ state }}</pre>
    </div>
</template>

<script>
import { reactive, toRefs } from 'vue'

export default {
  setup () {
    const state = reactive({
      parishes: [
        {
          text: 'Kingston',
          value: 'KGN'
        },
        {
          text: 'Portland',
          value: 'POR'
        },
        {
          text: 'Clarendon',
          value: 'CLA'
        }
      ],
      selectedParish: '',
      extras: {
        isCapital: false,
        hasManyTowns: false
      },
      attractions: '',
      attractionOptions: [
        { label: 'Yes', value: 1 },
        { label: 'No', value: 0 }
      ]
    })

    const handleUpdate = (val) => {
      if (val) {
        alert('This is on')
      } else {
        alert('This is off')
      }
    }
    return { ...toRefs(state), state, handleUpdate }
  }
}
</script>

<style scoped>

</style>
