<template>
  <div>Message from props: {{ props.msg }}</div>
  <button @click="handleEmit">Increase</button>
  <!-- <div>
    {{ $slots }}
  </div>
  <div>
    {{ $attrs }}
  </div> -->
  <slot> <div>Fallback content for Slot of ChildComp</div></slot>
</template>
<script setup>
const props = defineProps({ msg: String })
const emits = defineEmits(['click-to-increase']) // define arrays of emits
const handleEmit = () => {
  emits('click-to-increase', 1, 'hai', 'dfi') // emits('nameOfEmit',params)
}
</script>
<style></style>
