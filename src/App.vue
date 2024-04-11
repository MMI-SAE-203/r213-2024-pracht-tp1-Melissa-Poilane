<script setup lang="ts">
import { onErrorCaptured } from 'vue'
import { RouterLink, RouterView } from 'vue-router/auto'
import FooterPage from './components/FooterPage.vue' // Importez le composant FooterPage

onErrorCaptured((err, instance, info) => {
  console.error('erreur : ', err, '\ninfo : ', info, '\ncomposant : ', instance)
  return true
})
import { ref } from 'vue';

const menuIsOpen = ref(false)
</script>

<template>
  <header>
    <nav>
    <div>
<button
  aria-controls="mainNav"
  aria-expanded="true"
  class="rounded-full border-2 border-red-600 bg-red-300 px-2"
  @pointerdown="menuIsOpen = !menuIsOpen"
>
  menu
</button>
<Transition
  class="transition-transform duration-1000"
  enter-from-class="-translate-x-full"
  enter-to-class="translate-x-0"
  leave-active-class="-translate-x-full"
>
<nav v-show="menuIsOpen" id="mainNav">
  <ul>
    <li><RouterLink to="/" class="text-red-500 underline"> Accueil </RouterLink></li>
    <li><RouterLink to="/Accordéon1" class="text-red-500 underline"> Accordéon classique </RouterLink></li>
    <li><RouterLink to="/Accordéon2" class="text-red-500 underline"> Accordéon v-for </RouterLink></li>
  </ul>
</nav>
</Transition>
      <ul>
        <li>
        
        </li>
      </ul>
      </div>
    </nav>
  
  </header>
  <RouterView v-slot="{ Component }">
    <Suspense>
      <component :is="Component" />
    </Suspense>
  </RouterView>
  <FooterPage /> <!-- Utilisez le composant FooterPage ici -->
</template>