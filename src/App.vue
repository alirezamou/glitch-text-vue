<template>
  <GlitchText :text="revealingText" :speed="100" />
  <button @click="revealingText = 'Glitching text is cool'">Change the text</button>
</template>

<script>
import GlitchText from './components/GlitchText.vue';
export default {
  data() {
    return {
      revealingText: "this text has revealed"
    }
  },
  components: {
    GlitchText
  }
}
</script>