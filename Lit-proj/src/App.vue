<script lang="ts">
import Home from './components/Home.vue';
import Author from './components/Author.vue';
import Plot from './components/Plot.vue';
import Characters from './components/Characters.vue';
import Setting from './components/Setting.vue';
import Symbolism from './components/Symbolism.vue';
import Theme from './components/Theme.vue';
import NotFound from './components/NotFound.vue';

//make a type for routes
interface IRoutes {
  [key: string]: any
}
const routes: IRoutes = {
  '/': Home,
  '/Author': Author,
  '/Plot': Plot,
  '/Characters': Characters,
  '/Setting': Setting,
  'Symbolism': Symbolism,
  '/Theme': Theme
}

export default {
  data() {
    return {
      currentPath: window.location.hash,
      menu: false
    }
  },
  computed: {
    currentView() {
      return routes[this.currentPath.slice(1) || '/'] || NotFound
    }
  },
  mounted() {
    window.addEventListener('hashchange', () => {
		  this.currentPath = window.location.hash
		})
  }
}
</script>

<template class="h-full">
  <div>
    <div class="flex">
        <div v-if="menu" class="flex flex-col bg-slate-200 w-fit items-start">
          <!-- Nav enabled -->
          <button @click="menu = !menu"><span class="material-symbols-outlined">menu</span></button>
          <a href="#/" class="nav-button">Home</a>
          <a href="#/Author" class="nav-button">Author</a>
          <a href="#/Plot" class="nav-button">Plot</a>
          <a href="#/Characters" class="nav-button">Characters</a>
          <a href="#/Setting" class="nav-button">Setting</a>
          <a href="#/Symbolism" class="nav-button">Symbolism</a>
          <a href="#/Theme" class="nav-button">Theme</a>
        </div>
        <div v-else class="flex flex-col sm:h-screen bg-slate-200 w-10 items-start">
          <!-- Nav Disabled -->
          <button @click="menu = !menu"><span class="material-symbols-outlined">menu</span></button>
        </div>
    <div class="flex flex-col h-full">
        <div class="flex">
          <a href="#/" class="nav-button">Home</a>
          <a href="#/Author" class="nav-button">Author</a>
          <a href="#/Plot" class="nav-button">Plot</a>
          <a href="#/Characters" class="nav-button">Characters</a>
          <a href="#/Setting" class="nav-button">Setting</a>
          <a href="#/Symbolism" class="nav-button">Symbolism</a>
          <a href="#/Theme" class="nav-button">Theme</a>
      </div>
      <component :is="currentView" />
    </div>
  </div>
  
  </div>
</template>
