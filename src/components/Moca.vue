<script setup>

import { useSeek } from '@tresjs/core'
import { useGLTF } from '@tresjs/cientos'
import { ShaderMaterial } from 'three'

const { nodes } = await useGLTF('8-54-Stagger-moca_rooms_xyz.glb', { draco: true })


const model = nodes.mm_rooms_8slots_modelo

const { seekByName } = useSeek()
const outside = seekByName(model,'mm_rooms_8slots_modelo_primitive174')
console.log(outside)
outside.material = new ShaderMaterial({
      vertexShader: ``,
      fragmentShader:``
})
</script>

<template>
      <primitive :object="model" />
</template>

