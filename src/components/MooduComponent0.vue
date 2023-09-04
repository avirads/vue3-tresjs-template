<script setup>
import { ref } from 'vue'
import { useTexture } from '@tresjs/core'
import  MOCA  from './Moca.vue'

import {
  OrbitControls,
  TransformControls,
  Text3D,
  Stars
} from '@tresjs/cientos'

const boxRef1 = ref();
const boxRef2 = ref();
const boxRef3 = ref();

</script>

<template>


  <TresCanvas window-size>

    <Suspense>
      <MOCA />
    </Suspense>


    <TresPerspectiveCamera :args="[75,1,0.1,1000]" 
      :position="[1,1,18]"
      :look-at="[0,0,0]"
       @is-lock="state => isActive(state)"
    />

    <OrbitControls  make-default />
    <Stars />

    <Suspense>
      <Text3D
        :position="[0, 12, 0]"
        ref="textRef"
        font="FiraCodeRegular.json"
      >
        Denmark
        <TresMeshToonMaterial color="#FBB03B" />

      </Text3D>
    </Suspense>
    <TransformControls :object="boxRef1" mode="translate" />
    <TransformControls :object="boxRef2" mode="rotate" />
    <TransformControls :object="boxRef3" mode="scale" />

    <TresScene>
    <TresMesh ref="boxRef1"  :position="[-18, 1,0]">
      <TresBoxGeometry :args="[1, 1, 1]" />
      <TresMeshToonMaterial color="#FBB03B" />
    </TresMesh>    
      <TresMesh ref="boxRef2" :position="[0,1,-18]" :rotation="[0,Math.PI/6,0]">
        <TresBoxGeometry :args="[1,1,1]" />
        <TresMeshNormalMaterial color="blue" />
      </TresMesh>

      <TresMesh ref="boxRef3" :position="[18,1,0]" :rotation="[0,Math.PI/6,0]">
        <TresBoxGeometry :args="[1,1,1]" />
        <TresMeshBasicMaterial color="teal" />
      </TresMesh>

    </TresScene>
    <TresAxesHelper />
     <TresGridHelper :args="[20, 20]" />
    <TresAmbientLight :intensity="0.5" />
    <TresDirectionalLight :position="[0, 8, 4]" :intensity="1.5" cast-shadow />     
  </TresCanvas>

</template>

<style scoped>

</style>