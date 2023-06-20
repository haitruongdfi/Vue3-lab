<script setup>
import { ref } from 'vue'
import ChildComp from './components/ChildComp.vue'

let count = ref(0)
const sampleRef = ref(null)

function doSomething() {
  // this.$refs.sampleRef.style.backgroundColor =
  //   this.$refs.sampleRef.style.backgroundColor == 'aqua' ? 'blue' : 'aqua' // old style code
  // another way to use ref : https://vuejs.org/guide/essentials/template-refs.html#accessing-the-refs
  sampleRef.value.style.backgroundColor =
    sampleRef.value.style.backgroundColor == 'aqua' ? 'blue' : 'aqua'
  // use .value to unwrap ref object. If in the temlate, ref objects will be automatically unwrapped.
  //console.log(sampleRef)
}

// const handleEmitFromChild = (...args) => {
//   count.value += args[0]
//   console.log(args[1] + ' of ' + args[2])
// }
// or
const handleEmitFromChild = (a, name, company) => {
  count.value += a
  console.log(name + ' of ' + company)
}
</script>
<template>
  <header class="wrapper">
    <h1>Vue 3 Lab</h1>
    <p>{{ count }}</p>
    <ChildComp msg="Hello Vue Js" @click-to-increase="handleEmitFromChild">
      <div>This is a child message. It replaces the slot of child component</div>
    </ChildComp>
    <div ref="sampleRef">DOM with ref</div>
    <button @click="doSomething">Change bg color of Ref element</button>
  </header>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
