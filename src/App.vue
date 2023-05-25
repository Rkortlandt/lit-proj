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
  '/Symbolism': Symbolism,
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

<template class="Container">
  <div class="Container">
    <!-- <div class="flex w-screen">
      <div class="transform top-0 left-9 w-64 bg-slate-300 py-2 px-2 fixed h-full overflow-auto ease-in-out transition-all duration-300 z-30" :class="menu ? 'translate-x-0' : '-translate-x-full'">
        Nav enabled
        <button class="max-sm:hidden block" @click="menu = !menu"><span class="material-symbols-outlined">menu</span></button>
        <a href="#/" class="nav-button">Home</a>
        <a href="#/Author" class="nav-button">Author</a>    
        <a href="#/Plot" class="nav-button">Plot</a>
        <a href="#/Characters" class="nav-button">Characters</a>
        <a href="#/Setting" class="nav-button">Setting</a>
        <a href="#/Symbolism" class="nav-button">Symbolism</a>
        <a href="#/Theme" class="nav-button">Theme</a>
      </div>
      <div class="flex flex-col h-screen bg-slate-200 w-fit items-center z-40 sticky top-0 left-0">
        Nav Disabled
        <button class="CollapsedSideNavButton py-2 max-sm:block hidden px-2" @click="menu = !menu"><span class="material-symbols-outlined">menu</span></button>
        <button class="CollapsedSideNavButton py-2 max-sm:hidden block px-2" @click="menu = !menu"><span class="material-symbols-outlined">settings</span></button>
      </div>
      <div class="flex-grow">
        <div class="flex px-1 w-full sticky top-0 z-10">
          <button class="nav-button sm:hidden" @click="menu = !menu"><span class="material-symbols-outlined">menu</span></button>
          <a href="#/" class="nav-button">Home</a>
          <a href="#/Author" class="nav-button">Author</a>
          <a href="#/Plot" class="nav-button">Plot</a>
          <a href="#/Characters" class="nav-button">Characters</a>
          <a href="#/Setting" class="nav-button">Setting</a>
          <a href="#/Symbolism" class="nav-button">Symbolism</a>
          <a href="#/Theme" class="nav-button">Theme</a>
        </div>
        <component :is="currentView" class="flex-grow w-full h-screen"/>
      </div>
    </div> -->


  <!-- Nav -->
  <div class="Top-Nav">
    <div class="flex px-1 sticky top-0 left-10 z-10">
      <button class="nav-button sm:hidden" @click="menu = !menu"><span class="material-symbols-outlined">menu</span></button>
      <a href="#/" class="nav-button">Home</a>
      <a href="#/Author" class="nav-button">Author</a>
      <a href="#/Plot" class="nav-button">Plot</a>
      <a href="#/Characters" class="nav-button">Characters</a>
      <a href="#/Setting" class="nav-button">Setting</a>
      <!-- <a href="#/Symbolism" class="nav-button">Symbolism</a> -->
      <a href="#/Theme" class="nav-button">Theme</a>
    </div>
  </div>

  <!-- body -->
  <div class="Body fixed max-w-full overflow-scroll">
    <component :is="currentView" class="flex-grow w-full h-screen"/>
  </div>
  <!-- side-nav -->
  <div class="Side-Nav">
    <div class="transform top-0 left-0 w-64 bg-slate-300 py-2 px-2 fixed h-full overflow-auto ease-in-out transition-all duration-300 z-30" :class="menu ? 'translate-x-0' : '-translate-x-full'">
      <!-- Nav enabled -->
      <button class=" block py-2" @click="menu = !menu"><span class="material-symbols-outlined">menu</span></button>
      <a href="#/" class="side-nav-nav-button block">Home</a>
      <a href="#/Author" class="side-nav-nav-button block">Author</a>    
      <a href="#/Plot" class="side-nav-nav-button block">Plot</a>
      <a href="#/Characters" class="side-nav-nav-button block">Characters</a>
      <a href="#/Setting" class="side-nav-nav-button block">Setting</a>
      <!-- <a href="#/Symbolism" class="side-nav-nav-button block">Symbolism</a> -->
      <a href="#/Theme" class="side-nav-nav-button block">Theme</a>
    </div>
    <div class="flex flex-col h-fit rounded-br-xl shadow-lg bg-slate-200 w-fit items-center z-40 sticky top-0 left-0">
      <!-- Nav Disabled -->
      <button class="CollapsedSideNavButton py-2 max-sm:block hidden px-2" @click="menu = !menu"><span class="material-symbols-outlined">menu</span></button>
      <button class="CollapsedSideNavButton py-2 max-sm:hidden block px-2" @click="menu = !menu"><span class="material-symbols-outlined">settings</span></button>
    </div>


  </div>
</div>  
</template>