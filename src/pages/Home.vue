<template>
  <TheNavigation :nav-links="navLinks" />
  <AppButton
    primary
    text="Get Started"
    class="header-button"
    link="#palettes"
  />
  <main>
    <section
      id="abtus"
      class="about-us section"
    >
      <div class="wrapper">
        <h2 class="section-title">
          About the Project
        </h2>
        <p class="section-text">
          Welcome Terrarians, this site has been built to make building cool projects a little bit easier.
          We prepared many palettes for you to look up and use.
          Each palette has fitting <span>tags</span> (in terms of style usage) and <span>obtainability</span> - an attribute deciding how hard it is to get all the neccessary items. 
        </p>
        <p class="section-text">
          Additionally, <span>YOU</span> can also help the community by <a href="#your_ideas">submitting your own ideas!</a>
        </p>
        <p class="section-text">
          Also, if you are curious of the creators, click the button below :)
        </p>
        <AppButton
          secondary
          text="Meet the Team"
          class="w-max mt-7"
          @click="router.push({ name: 'Team' })"
        />
      </div>
    </section>
    <SectionPalettes
      ref="palettesSection"
      :palettes="paletteStore.palettes"
    />
    <SectionYourIdeas />
  </main>
</template>

<script setup>
import { onMounted } from 'vue'
import { useRouter } from 'vue-router'
import { usePaletteStore } from '@/stores/PaletteStore.js'
import setScrollPadding from '@/js/setScrollPadding'
import TheNavigation from '@/components/TheNavigation.vue'
import SectionPalettes from '@/components/SectionPalettes.vue'
import SectionYourIdeas from '@/components/SectionYourIdeas.vue'
const paletteStore = usePaletteStore()
const router = useRouter()
const navLinks = [
  {
    text: 'About Us',
    href: 'abtus',
    isSamePage: true
  },
  {
    text: 'Team',
    componentName: 'Team',
    href: '',
    isSamePage: false
  },
  {
    text: 'Palettes',
    href: 'palettes',
    isSamePage: true
  },
  {
    text: 'Your Ideas',
    href: 'your_ideas',
    isSamePage: true
  }
]
onMounted(async () => {
  setScrollPadding()
})
</script>

<style lang="scss" scoped>
.header-button {
  position: absolute;
  top: 80vh;
  left: 50%;
  transform: translateX(-50%);
  width: max-content;
  z-index: 30;
}
</style>