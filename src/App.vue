<template>
  <div class="wrap">
    <div class="player">
      <select v-model="activeRadio" class="select" @change="changeSource">
        <option v-for="(radio, idx) in sources" :key="idx" :value="radio.source">
          {{radio.name}}
        </option>
      </select>
      <br>
      <audio controls ref="audio">
        <source :src="activeRadio" type="audio/mpeg">
      </audio>
    </div>
  </div>
</template>

<script>
import sources from './sources'

export default {
  name: 'App',
  data: () => ({
    activeRadio: {},
    sources: []
  }),
  methods: {
    changeSource() {
      const audio = this.$refs.audio
      audio.load()
      audio.play() 
    }
  },
  created () {
    this.sources = sources
  }
}
</script>

<style>
  .wrap {
    height: 100vh;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .select {
    width: 340px;
    height: 30px;
  }
</style>
