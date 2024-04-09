<script setup lang="ts">
import { ref } from 'vue';

const maVar = ref(false);
</script>

<template>
  <button @pointerdown="maVar = !maVar">Menu</button>

<button
  aria-controls="mainNav"
  aria-expanded="true"
  class="rounded-full border-2 border-red-600 bg-red-300 px-2"
>
  menu
</button>
<!-- nav#mainNav>ul>li*3>a[href="#"]{item $} -->
<nav id="mainNav">
  <ul>
    <li><a href="#">item 1</a></li>
    <li><a href="#">item 2</a></li>
    <li><a href="#">item 3</a></li>
  </ul>
</nav>

  <h1 v-show="maVar" class="text-2xl">Bonjour le monde !</h1>
</template>
