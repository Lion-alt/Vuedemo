

<script>
export default {
  name: "SleepMood",
  data () {
    return {
      innerMood: 'Sleep'
    }
  },
  computed: {
    dinoMood() {
      return `Dino${this.innerMood}`
    }
  },
  methods : {
    updatePetMood () {
      this.$emit('update-pet-mood')
    }
  }
}
</script>

<style scoped>

</style>