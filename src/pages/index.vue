<script setup lang="ts">
import { ref } from 'vue';

const menuIsOpen = ref(false)
const sectionOpen = ref(1)
const sectionsData = [
  {
    label: 'bouton 1',
    texte: `texte panneau 1 Lorem ipsum dolor sit ame
    consectetur adipisicing elit. Inventore animi dolore,
    rerum magni laudantium quod excepturi laboriosam, 
    ex modi debitis harum reprehenderit eaque quam ut
    ea molestiae. Id, cum dolor!`
  },
  {
    label: 'bouton 2',
    texte: `texte panneau 2 Amet alias provident quos quis, 
    Officia ut ab dolores quos dolorem accusamus ad,
    consectetur unde minima, ipsum eligendi inventore id
    labore, laborum rerum laboriosam corrupti iste.
    Distinctio, perspiciatis!`
  },
  {
    label: 'bouton 3',
    texte: `texte panneau 3 Repudiandae corporis voluptates, 
    odit reprehenderit sint pariatur at voluptatum, cumque
    quia sit eligendi ex culpa eos, alias magnam molestiae
    id modi accusantium ipsa eveniet accusamus. Tempora 
    quis corporis et nam.`
  }
]
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

  <section >
    <button class="text-xl" @pointerdown="sectionOpen = sectionOpen === 1 ? 0 : 1">bouton 1 </button>
    <p v-show="sectionOpen === 1">Lorem ipsum dolor sit amet consectetur adipisicing elit. Asperiores hic, pariatur sed veritatis tempore atque ducimus natus sapiente eveniet, corporis laborum ullam eaque dignissimos at iste dolore consequuntur? Blanditiis, labore.</p>
  </section>
  <section >
    <button class="text-xl" @pointerdown="sectionOpen = sectionOpen === 2 ? 0 : 2">bouton 2</button>
    <p v-show="sectionOpen === 2">Error quae itaque iste molestiae ipsum earum voluptas similique delectus atque laborum consectetur et non consequatur ex nihil, repudiandae alias necessitatibus nemo nisi? Reiciendis, modi quia ipsum ratione dolorem ut!</p>
  </section>
  <section >
    <button class="text-xl" @pointerdown="sectionOpen = sectionOpen === 3 ? 0 : 3">bouton 3</button>
    <p v-show="sectionOpen === 3">Fuga, ea adipisci omnis dolore autem veniam reiciendis voluptate praesentium repellat aperiam ipsa, tempore voluptatibus? Ab, ea est! Eum voluptates at deserunt error accusamus omnis cum voluptatem incidunt dicta dolore.</p>
  </section>

  <div v-for="(section, key) in sectionsData" :key="key">
  <button class="accordion" @click="toggleAccordion(key)">
    {{ section.label }}
  </button>
  <div class="panel" v-show="activeAccordion === key">
    <p>{{ section.texte }}</p>
  </div>
</div>

</template>
