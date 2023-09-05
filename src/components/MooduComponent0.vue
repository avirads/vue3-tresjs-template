<script setup>
import { ref } from 'vue'
import { useTexture } from '@tresjs/core'
import  MOCA  from './Moca.vue'

import {
  MapControls,
  OrbitControls,
  PointerLockControls,
  KeyboardControls,
  TransformControls,
  CameraControls,
  Text3D,
  Stars,
  useEnvironment,
  Environment 
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

  <Environment files="industrial_sunset_puresky_2k.hdr" background='true' />
    <TresPerspectiveCamera :args="[75,1,0.1,1000]" 
      :position="[1,2,18]"
      :look-at="[0,0,0]"
       @is-lock="state => isActive(state)"
    />

   <!--    
   <CameraControls />

    <MapControls />
   <OrbitControls  make-default />

    <PointerLockControls />
    <KeyboardControls />    
    -->
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
    <TransformControls :object="boxRef1" mode="translate" size="0.2" />
    <TransformControls :object="boxRef2" mode="rotate"  size="0.2" />
    <TransformControls :object="boxRef3" mode="scale"  size="0.2"  />

    <TresScene>
    <TresMesh ref="boxRef1"  :position="[-18, 1,0]">
      <TresBoxGeometry :args="[1, 1, 1]" />
      <TresMeshToonMaterial color="#FBB03B" />
    </TresMesh>    
      <TresMesh ref="boxRef2" :position="[0,0,12]" :rotation="[0,Math.PI/6,0]">
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
