<script setup lang="ts">
import { TresCanvas } from '@tresjs/core'
import { OrbitControls } from '@tresjs/cientos'
</script>

<template>
  <TresCanvas clear-color="#82DBC5">
    <TresPerspectiveCamera
      :position="[4, 4, 4]"
      :look-at="[0, 1, 0]"
    />
    <OrbitControls />
    <TresScene>
      <TresMesh
        :position="[0, 1, 0]"
        :scale="[2, 0.5, 1]"
        :rotate-x="Math.PI / 4"
      >
        <TresBoxGeometry
          :args="[1, 1, 1]"
        />
        <TresMeshNormalMaterial />
      </TresMesh>
    </TresScene>
    <TresAxesHelper />
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