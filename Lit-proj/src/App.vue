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

<template class="h-full w-full">
  <div>
    <div class="flex w-full">
        <div class="transform top-0 left-9 w-64 bg-white fixed h-full overflow-auto ease-in-out transition-all duration-300 z-30" :class="menu ? 'translate-x-0' : '-translate-x-full'">
          <!-- Nav enabled -->
          <button class="max-sm:block hidden" @click="menu = !menu"><span class="material-symbols-outlined">menu</span></button>
          <a href="#/" class="nav-button">Home</a>
          <a href="#/Author" class="nav-button">Author</a>
          <a href="#/Plot" class="nav-button">Plot</a>
          <a href="#/Characters" class="nav-button">Characters</a>
          <a href="#/Setting" class="nav-button">Setting</a>
          <a href="#/Symbolism" class="nav-button">Symbolism</a>
          <a href="#/Theme" class="nav-button">Theme</a>
        </div>
        <div class="flex flex-col h-screen max-sm:hidden bg-slate-200 w-10 items-center z-40">
          <!-- Nav Disabled -->
          <button class="CollapsedSideNavButton my-1 bg-emerald-500 px-1 pt-1 rounded-lg" @click="menu = !menu"><span class="material-symbols-outlined">menu</span></button>
        </div>
    <div class="flex flex-col h-full">
        <div class="flex px-1 w-full">
          <button class="nav-button sm:hidden" @click="menu = !menu"><span class="material-symbols-outlined">menu</span></button>
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
