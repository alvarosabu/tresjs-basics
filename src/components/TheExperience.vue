<script setup lang="ts">
import { TresCanvas } from '@tresjs/core'
import { OrbitControls } from '@tresjs/cientos'
</script>

<template>
  <TresCanvas clear-color="#82DBC5">
    <TresPerspectiveCamera />
    <OrbitControls />
    <TresMesh>
      <TresTorusGeometry :args="[1, 0.4, 32, 32]" />
      <TresMeshToonMaterial color="hotpink" />
    </TresMesh>
    <TresAxesHelper />
    <TresDirectionalLight :position="[-1, 2, 4]" />
  </TresCanvas>
</template>

<style>
html,
body,
#app {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
}
</style>