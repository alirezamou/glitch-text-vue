<template>
  <GlitchText text="alireza" />
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