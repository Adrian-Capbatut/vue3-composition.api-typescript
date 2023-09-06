<script setup lang="ts">
import GameHeader from './components/GameHeader.vue'
import GameFigure from './components/GameFigure.vue'
import GameWrongLetters from './components/GameWrongLetters.vue'
import GameWord from './components/GameWord.vue'
import GamePopup from './components/GamePopup.vue'
import GameNotification from './components/GameNotification.vue'
import { ref } from 'vue'

const word = ref('василий')
const letters = ref<string[]>([])

window.addEventListener('keydown', ({ key }) => {
  if (/[а-яА-ЯёЁ]/.test(key)) {
    letters.value.push(key.toLowerCase())
  }
})
</script>

<template>
  {{ word }}
  {{ letters }}
  <GameHeader />

  <div class="game-container">
    <GameFigure />

    <GameWrongLetters />

    <GameWord :word="word" />
  </div>

  <!-- Container for final message -->
  <GamePopup v-if="false" />

  <!-- Notification -->
  <GameNotification />
</template>
