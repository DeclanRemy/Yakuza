<script setup lang="ts">

import IconX from "@/components/icons/IconX.vue";

const emit = defineEmits(['close']);

</script>

<template>
  <div id="modal-background" class="modal-background">
    <div class="modal max-w-screen-xs mx-auto">
      <div class="title">
        <div class="subtitle">
          <h2 id="modal-title">about</h2>
        </div>
        <div class="close-button">
          <button class="border-none text-custom-mg" v-on:click="emit('close')">
            <IconX/>
          </button>
        </div>
      </div>
      <div class="text">
        <slot/>
      </div>
    </div>
  </div>
</template>

<style scoped>
.title {
  display: flex;

  justify-content: center;
  align-items: center;

  margin-bottom: 1.5rem;
}

.subtitle{
  flex: 1 1 0%;
  padding-left: 1.75rem;
}

.close-button{
  display: flex;
  justify-self: end;
}

.close-button button{
  color: var(--color-mg);
  border-style: none;
}

.close-button button svg{
  width: 1.75rem;
  height: 1.75rem;
}

.subtitle h2 {
  text-indent: 0.25em;
  color: var(--color-line);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  font-weight: 10;
  font-size: 1.75rem;
  line-height: 1.15rem;
  text-align: center;
}

.modal{
  border-radius: 0.125rem;
  width: 100%;
  top: 5rem;
  position: relative;
  pointer-events: auto;

  background: var(--color-modal-bg);

  border-color: var(--color-modal-border);
  border-width: 1px;

  padding: 1.5rem;
}

.modal-background{
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.65);
  z-index: 1000;
}
</style>