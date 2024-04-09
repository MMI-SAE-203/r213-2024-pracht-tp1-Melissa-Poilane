<script setup lang="ts">
import { ref } from 'vue';

const menuIsOpen = ref(false)
</script>

<template>

<button
  aria-controls="mainNav"
  aria-expanded="true"
  class="rounded-full border-2 border-red-600 bg-red-300 px-2"
  @pointerdown="menuIsOpen = !menuIsOpen"
>
  menu
</button>
<!-- nav#mainNav>ul>li*3>a[href="#"]{item $} -->
<Transition
  class="transition-transform duration-1000"
  enter-from-class="-translate-x-full"
  enter-to-class="translate-x-0"
  leave-active-class="-translate-x-full"
>
<nav v-show="menuIsOpen" id="mainNav">
  <ul>
    <li><a href="#">item 1</a></li>
    <li><a href="#">item 2</a></li>
    <li><a href="#">item 3</a></li>
  </ul>
</nav>
</Transition>

  <h1 class="text-2xl">Bonjour le monde !</h1>
</template>
