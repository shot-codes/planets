<script lang="ts">
  import type { PerspectiveCamera } from "three";
  import type { Rotation } from "@threlte/core";
  import { OrbitControls, T, useFrame } from "@threlte/core";
  import { Environment, Text, HTML } from "@threlte/extras";
  import LaminaMesh from "$lib/LaminaMesh.svelte";

  const text = "hi";
  let camera: PerspectiveCamera;
  let camera_rotation: Rotation;
  useFrame(() => {
    camera_rotation = camera.rotation;
  });
</script>

<Environment
  path="/"
  files="nebula_low_res.hdr"
  isBackground={true}
  format="hdr"
/>

<T.AmbientLight intensity={0.15} />

<T.PerspectiveCamera
  makeDefault
  position={[0, 3, 5]}
  fov={90}
  bind:ref={camera}
>
  <OrbitControls enableDamping target={{ y: 0.5 }} />
</T.PerspectiveCamera>

<LaminaMesh />

<!-- <T.Group>
  <Text
    {text}
    position={{ y: 2.7 }}
    rotation={camera_rotation}
    scale={5}
    textAlign="center"
    anchorX="center"
  />
  <T.Mesh castShadow receiveShadow position.y={1}>
    <T.SphereGeometry />

    <T.MeshStandardMaterial
      color="#ffffff"
      metalness={0.9}
      roughness={0.05}
      envMapIntensity={0.5}
    />
  </T.Mesh>
</T.Group> -->
