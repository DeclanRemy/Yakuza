<script setup lang="ts">
import settings from "@/settings/settings.json";
import { currentGameState } from "@/main";

function getType(i: number) : String{
  let guess = currentGameState.value.guessed[i-1];
  if(guess === undefined) { return 'free'; }

  if(guess.name === "Skipped") return "skipped";

  if(guess.isCorrect) return "success";
  else return "failed";
}

</script>

<template>
  <div class="container flex justify-center my-2">
    <div v-for="i in settings['guess-number']" v-if="currentGameState !== undefined" class="guess-value" :type="getType(i)" ></div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;

  margin: 0.5rem 0;
}

.guess-value {
  width: 1rem;
  height: 0.25rem;
  margin: 0.125rem;

  &[type=success]{
    background: var(--color-positive);
  }

  &[type=failed]{
    background: var(--color-negative);
  }

  &[type=skipped]{
    background: var(--color-mg);
  }

  &[type=free]{
    background: var(--color-fg);
  }
}
</style>