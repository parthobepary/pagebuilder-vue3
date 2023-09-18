<template>
  <div>
    <div class="root">
      <div class="container">
        <button ref="targetRef"
                v-bind:style="{ 'height':block.data.buttonHeight + 'px', 'width':block.data.buttonWidth + 'px' ,'font-size':  block.data.buttonFontSize + 'px', 'background-color': block.data.buttonBgColor, 'color': block.data.buttonTextColor  }"
                class=" btn btn-block  btn-lg text-xl target">
          {{ block.data.buttonText }}
        </button>
        <Moveable
            :target="targetRef"
            :draggable="draggable"
            :throttleDrag="throttleDrag"
            :edgeDraggable="edgeDraggable"
            :startDragRotate="startDragRotate"
            :throttleDragRotate="throttleDragRotate"
            @drag="onDrag"/>
      </div>
    </div>
  </div>
  <!--  <div :class="{'bg-gray-900 text-gray-100': block.data.darkMode, 'bg-white': !block.data.darkMode}">-->
  <!--    <div class="max-w-6xl mx-auto">-->
  <!--      <divv-bind:style="{ 'color': color, 'font-size': fontSize + 'px','background-color':bgColor }" :class="{'py-6 md:pt-12 pb-24': first, 'py-12 md:py-24': !first}" class="px-4 md:px-8">-->
  <!--        <div class="grid grid-cols-12 space-y-8">-->
  <!--          <div class="col-span-12">-->
  <!--            <h2 class="text-3xl md:text-4xl font-bold">-->
  <!--              {{ block.data.title }}-->
  <!--            </h2>-->
  <!--          </div>-->
  <!--          <div class="col-span-12">-->
  <!--            <div class="grid grid-cols-12 items-center space-y-8">-->
  <!--              <div class="col-span-12 md:col-span-5 order-1 md:order-2">-->
  <!--                <img :src="block.data.imageUrl" class="block mx-auto max-h-72 max-w-fit p-6 md:p-2" loading="lazy">-->
  <!--              </div>-->
  <!--              <div class="col-span-12 md:col-span-7 order-2 md:order-1">-->
  <!--                <p class="font-light tracking-wide text-lg break-words">-->
  <!--                  {{ block.data.description }}-->
  <!--                </p>-->
  <!--              </div>-->
  <!--            </div>-->
  <!--          </div>-->
  <!--        </div>-->
  <!--      </div>-->
  <!--    </div>-->
  <!--  </div>-->
</template>

<script>
import {defineComponent} from 'vue'
import {ref} from "vue";
import Moveable from "vue3-moveable";


export default defineComponent({
  name: 'PrimaryButton',
  components: {
    Moveable
  },
  props: {
    block: {
      type: Object,
      required: true
    },
    first: {
      type: Boolean,
      default: false
    }
  },
  setup() {
    const draggable = true;
    const throttleDrag = 1;
    const edgeDraggable = false;
    const startDragRotate = 0;
    const throttleDragRotate = 0;
    const targetRef = ref(null);
    const onDrag = e => {
      e.target.style.transform = e.transform;
    };
    return {
      targetRef,
      draggable,
      throttleDrag,
      edgeDraggable,
      startDragRotate,
      throttleDragRotate,
      onDrag
    };
  }
})
</script>

<style>
.moveable-target {
  width: 100px;
  height: 100px;
  background-color: lightblue;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}
</style>
