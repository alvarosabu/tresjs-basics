<script setup lang="ts">

</script>
<template>
    <TresCanvas window-size>
        <TresPerspectiveCamera :args="[75, 1, 0.1, 1000]"
            :position="[3, 1, 4]" :look-at="[0, 0, 0]"
        />
        <TresScene>
            <TresMesh :position="[0, 2, 0]" :rotation="[0, Math.PI / 6,Math.PI / 6]">
                <TresBoxGeometry :args="[1,1,1]" />
                <TresMeshNormalMaterial  />
            </TresMesh>
        </TresScene>
        <TresAxesHelper />
    </TresCanvas>
</template>