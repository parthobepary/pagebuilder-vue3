<template>
  <div class="space-y-2">
    <div class="form-control">
      <label class="cursor-pointer label flex justify-start">
        <input v-model="block.data.darkMode" type="checkbox" checked="checked" class="toggle toggle-primary">
        <span class="label-text text-base ml-2">Dark mode</span>
      </label>
    </div>
    <div class="form-control">
      <label class="label -mb-2">
        <span class="label-text">Button Text</span>
      </label>
      <input v-model="block.data.buttonText" type="text" class="input input-bordered input-sm">
    </div>
    <div class="form-control">
      <label class="label -mb-2">
        <span class="label-text">Button link</span>
      </label>
      <input v-model="block.data.buttonLink" type="text" class="input input-bordered input-sm">
    </div>
    <div class="form-control">
      <label class="label -mb-2">
        <span class="label-text">Button Width</span>
      </label>
      <input v-model="block.data.buttonWidth" type="number" class="input input-bordered input-sm">
    </div>
    <div class="form-control">
      <label class="label -mb-2">
        <span class="label-text">Button Height</span>
      </label>
      <input v-model="block.data.buttonHeight" type="number" class="input input-bordered input-sm">
    </div>
    <div class="form-control">
      <label class="label -mb-2">
        <span class="label-text">Button Text Size</span>
      </label>
      <input v-model="block.data.buttonFontSize" type="number" class="input input-bordered input-sm">
    </div>
    <div class="form-control">
      <label class="label -mb-2">
        <span class="label-text">Button Color</span>
      </label>
      <input v-model="block.data.buttonBgColor" type="color" class="input input-bordered input-sm">
    </div>
    <div class="form-control">
      <label class="label -mb-2">
        <span class="label-text">Button Text Color</span>
      </label>
      <input v-model="block.data.buttonTextColor" type="color" class="input input-bordered input-sm">
    </div>
  </div>
</template>

<script>
import { defineComponent, computed } from 'vue'
import ImageSelect from '../../ImageSelect.vue'

export default defineComponent({
  name: 'PrimaryButtonOptions',
  emits: ['update:modelValue'],
  components: {
    ImageSelect,
  },
  props: {
    modelValue: {
      type: Object,
      default: () => ({}),
    }
  },
  setup(props, context) {
    const block = computed({
      get: () => props.modelValue,
      set: (value) => context.emit('update:modelValue', value),
    })

    return { block }
  },
})
</script>
