<script setup>

import { useSeek } from '@tresjs/core'
import { useGLTF } from '@tresjs/cientos'
import { ShaderMaterial } from 'three'

const { nodes } = await useGLTF('rooms_8-54-Stagger-moca_rooms_xyz.glb', { draco: true })

console.log(nodes)
const model = nodes.Empty

const { seekByName } = useSeek()

/*
const outside = seekByName(model,'Slot_001')
console.log(outside)
outside.material = new ShaderMaterial({
      vertexShader: ``,
      fragmentShader:``
})
*/
</script>

<template>
      <primitive :object="model" />
</template>

