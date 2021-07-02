<template>
    <div id="dynamic-component-demo" class="demo">
      <button
          v-for="tab in $data.tabs"
          v-bind:key="tab"
          v-bind:class="['tab-button', { active: currentTab === tab }]"
          v-on:click="currentTab = tab"
      >
        {{ tab }}
      </button>

      <component v-bind:is="currentTabComponent" class="tab"></component>
      <DinoPet :mood="parentPetMood" @update-pet-mood="changePetMood"></DinoPet>
      <p>{{ parentPetMood }}</p>
    </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import tabHome from './components/tabHome.vue'
import tabPosts from './components/tabPosts.vue'
import tabArchive from './components/tabArchive.vue'
import DinoPet from './components/CustomEvents/DinoPet.vue'


export default({
  name: 'App',
  components: {
    HelloWorld, tabHome, tabPosts, tabArchive, DinoPet
  },
  props: {
    petMood: {
      type: String
    }
  },
  data() {
    return {
      currentTab: 'Home',
      tabs: ['Home', 'Posts', 'Archive'],
      parentPetMood : ''
    }
  },
  methods : {
    changePetMood(payload) {
      this.parentPetMood = payload.mood
    }
  },
  computed: {
    currentTabComponent() {
      return 'tab-' + this.currentTab.toLowerCase()
    }
  }
})

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
