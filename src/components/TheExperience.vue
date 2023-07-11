<script setup lang="ts">
import { SRGBColorSpace } from 'three'
import { TresCanvas } from '@tresjs/core'
import { OrbitControls } from '@tresjs/cientos'

// Buffer Geometry
/* const positionsArray = new Float32Array([
  0, 0, 0, // First Vertice
  0, 1, 0, // Second Vertice
  1, 0, 0, // Third Vertice
  1, 1, 0,
  1, 0, 0,
  1, 1, 0,
]) */
</script>

<template>
  <TresCanvas
    clear-color="#2c3846"
    :output-color-space="SRGBColorSpace"
  >
    <TresPerspectiveCamera />
    <OrbitControls />
    <TresMesh>
      <TresTorusKnotGeometry />
      <TresMeshNormalMaterial />
    </TresMesh>
    <!-- <TresMesh>
      <TresBufferGeometry
        :position="[positionsArray, 3]"
      />
      <TresMeshBasicMaterial
        color="#ff0000"
        wireframe
      />
    </TresMesh> -->
    <TresAxesHelper :args="[0.5]" />
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