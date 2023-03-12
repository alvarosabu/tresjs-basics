<script setup lang="ts">
import { useRenderLoop } from '@tresjs/core';
import { ref, watch } from 'vue';

const boxRef = ref();
const boxPosition = ref([0, 0, 0]);

const { onLoop } = useRenderLoop();

onLoop(({ delta, elapsed}) => {
    if (!boxRef.value) return;

    boxPosition.value[0] += delta;

    /* boxRef.value.rotation.z += delta;
    boxRef.value.rotation.y = elapsed; */
});
</script>
<template>
    <TresCanvas window-size>
        <TresPerspectiveCamera :args="[75, 1, 0.1, 1000]"
            :position="[3, 1, 4]" :look-at="[0, 0, 0]"
        />
        <TresScene>
            <TresMesh ref="boxRef" :position="boxPosition">
                <TresBoxGeometry :args="[1,1,1]" />
                <TresMeshNormalMaterial  />
            </TresMesh>
        </TresScene>
        <TresAxesHelper />
    </TresCanvas>
</template>