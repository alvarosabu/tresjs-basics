<script setup lang="ts">
import { Vector3 } from 'three'
import { TresCanvas } from '@tresjs/core'
import { OrbitControls, vLightHelper, vAlwaysLookAt } from '@tresjs/cientos'
import { useControls, TresLeches } from '@tresjs/leches'
import '@tresjs/leches/styles'
import { ref } from 'vue'

const directionalLight = ref()
const { value: position } = useControls({
  position: new Vector3(-3, 3, 3),
})

const { value: distance } = useControls({
  distance: 19,
})

const { value: decay } = useControls({
  decay: 1,
})

const { value: penumbra } = useControls({
  penumbra: 2,
})
</script>

<template>
  <TresLeches />
  <TresCanvas
    clear-color="black"
    shadows
  >
    <TresPerspectiveCamera :position="[10, 5, 10]" />
    <OrbitControls />
    <TresGroup :position="[0, 2, 0]">
      <TresMesh
        cast-shadow
        receive-shadow
      >
        <TresTorusGeometry :args="[1, 0.4, 32, 32]" />
        <TresMeshStandardMaterial color="white" />
      </TresMesh>
      <TresMesh
        :position="[2, 2, 1]"
        cast-shadow
      >
        <TresBoxGeometry :args="[2, 2, 2]" />
        <TresMeshStandardMaterial color="white" />
      </TresMesh>
      <TresMesh
        :position="[-4, 0, 0]"
        cast-shadow
      >
        <TresTorusKnotGeometry :args="[1, 0.4, 32, 32]" />
        <TresMeshStandardMaterial
          color="white"
          :roughness="0.1"
        />
      </TresMesh>
    </TresGroup>
    <TresMesh
      :rotate-x="-Math.PI / 2"
      receive-shadow
    >
      <TresPlaneGeometry :args="[15, 15]" />
      <TresMeshStandardMaterial color="white" />
    </TresMesh>
    <TresDirectionalLight
      ref="directionalRef"
      v-light-helper 
      :args="['white', 2]"
      :position="[5, 8, 3]"
      cast-shadow
      :shadow-map-size-width="2048"
      :shadow-map-size-height="2048"
      :shadow-camera-near="0.1"
      :shadow-camera-far="100"
      :shadow-radius="10"
    />
    <TresHemisphereLight :args="['red', 'blue', 0.5]" />
    <TresSpotLight
      v-light-helper
      :args="['#ffffff', 4]"
      :distance="distance"
      :decay="decay"
      :position-x="position.x"
      :position-y="position.y"
      :position-z="position.z"
      :penumbra="penumbra"
      cast-shadow
      :shadow-radius="1"
    />
    <TresRectAreaLight 
      v-always-look-at="[-4, 0, 0]" 
      :args="['hotpink', 2, 5, 5]"
      :position="[0, 1, 2]"
      cast-shadow
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