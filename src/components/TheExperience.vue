<script setup lang="ts">
import { SRGBColorSpace } from 'three'
import { TresCanvas } from '@tresjs/core'
import { OrbitControls } from '@tresjs/cientos'
</script>

<template>
  <TresCanvas
    clear-color="white"
    :output-color-space="SRGBColorSpace"
    alpha
  >
    <TresPerspectiveCamera />
    <OrbitControls />
    <!-- <TresMesh>
      <TresTorusKnotGeometry :args="[1, 0.4, 32, 32]" />
      <TresMeshPhysicalMaterial
        color="teal"
        :roughness="0.2"
      />
    </TresMesh> -->
    <TresMesh :position="[-4, 0, 0]">
      <TresTorusGeometry :args="[1, 0.4, 32, 32]" />
      <TresMeshPhongMaterial color="teal" wireframe />
    </TresMesh>
    <TresMesh :position="[0, 0, 0]">
      <TresTorusGeometry :args="[1, 0.4, 32, 32]" />
      <TresMeshNormalMaterial color="cyan" />
    </TresMesh>
    <TresMesh :position="[4, 0, 0]">
      <TresTorusGeometry :args="[1, 0.4, 32, 32]" />
      <TresMeshToonMaterial color="hotpink" />
    </TresMesh>
    <TresAmbientLight :args="[0xffffff, 1]" />
    <TresDirectionalLight
      :args="[0xffffff, 0.5]"
      :position="[0, 4, 4]"
    />
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