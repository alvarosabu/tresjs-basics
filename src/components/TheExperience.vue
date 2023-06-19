<script setup lang="ts">
import { TresCanvas, useRenderLoop } from '@tresjs/core'
import { OrbitControls } from '@tresjs/cientos'
import { shallowRef } from 'vue'

// Use TemplateRef to access the THREE instance you want to animate
const cubeRef = shallowRef<THREE.Mesh>()
const { onLoop } = useRenderLoop()

// Use onLoop to run a function on every frame
onLoop(({ delta, elapsed }) => {
  // Use the THREE instance to animate
  if (!cubeRef.value) return

  cubeRef.value.rotation.y += delta
  cubeRef.value.rotation.z = elapsed

  // Animate using trigonometry
  cubeRef.value.position.y = Math.sin(elapsed) * 2
  cubeRef.value.scale.set(
    Math.sin(elapsed) * 2,
    Math.sin(elapsed) * 2,
    Math.sin(elapsed) * 2,
  )

})
</script>

<template>
  <TresCanvas clear-color="#82DBC5">
    <TresPerspectiveCamera />
    <OrbitControls />
    <TresMesh ref="cubeRef">
      <TresBoxGeometry :args="[1, 1, 1]" />
      <TresMeshNormalMaterial />
    </TresMesh>
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