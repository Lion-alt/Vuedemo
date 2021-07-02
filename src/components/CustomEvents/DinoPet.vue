<template>
    <div>
      <component :is="dinoMood" />
      <button @click="updatePetMood">Sleep</button>
      <component :is="dinoHungryMood" />
      <button @click="updatePetMoodToHungry">Hungry</button>
      <component :is="dinoHappyMood" />
      <button @click="updatePetMoodToHappy">Happy</button>
    </div>
</template>

<script>




export default {
  name: "DinoPet",
  data() {
    return {
      innerMood : 'Sleep',
      hungryMood : 'Hungry',
      happyMood : 'Happy'
    }
  },
  computed: {
    dinoMood() {
      return `Dino${this.innerMood}`
    },
    dinoHungryMood() {
      return `Dino${this.hungryMood}`
    },
    dinoHappyMood() {
      return `Dino${this.happyMood}`
    }
  },
  emits : ['update-pet-mood'],
  methods : {
    updatePetMood () {
      this.$emit('update-pet-mood', {
        mood: this.innerMood
      })
    },
    updatePetMoodToHungry() {
      this.$emit('update-pet-mood', {
        mood: this.hungryMood
      })
    },
    updatePetMoodToHappy () {
      this.$emit('update-pet-mood', {
        mood: this.happyMood
      })
    }
  }
}


</script>

<style scoped>


</style>