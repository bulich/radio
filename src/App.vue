<template>
  <div class="wrap">
    <div class="player">
      <select v-model="activeRadio" class="select" @change="changeSource">
        <option v-for="(radio, idx) in sources" :key="idx" :value="radio.source">
          {{radio.name}}
        </option>
      </select>
      <br>
      <audio controls ref="audio" class="audio">
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
  .player {
    background: #f1f3f4;
    padding: 20px;
    border-radius: 20px;
    box-shadow: 0px 4px 18px #D5D8E0;
  }
  .wrap {
    height: 100vh;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .select {
    width: 284px;
    padding: 0 15px;
    height: 40px;
    background: none;
    border: none;
  }

  .select:focus,
  .select:active,
  .audio:focus,
  .audio:active {
    outline: none;
    border: none;
  }
</style>
