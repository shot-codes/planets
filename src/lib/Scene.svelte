<script lang="ts">
  import type { PerspectiveCamera } from "three";
  import type { Rotation } from "@threlte/core";
  import { OrbitControls, T, useFrame } from "@threlte/core";
  import { Environment, Text, HTML } from "@threlte/extras";
  import { degToRad } from "three/src/math/MathUtils";

  const text = "hi";
  let camera: PerspectiveCamera;
  let camera_rotation: Rotation;
  useFrame(() => {
    camera_rotation = camera.rotation;
  });
</script>

<Environment
  path="/"
  files="bball.hdr"
  isBackground={true}
  format="hdr"
  groundProjection={{
    radius: 75,
    height: 5,
    scale: { x: 200, y: 200, z: 200 },
  }}
/>

<T.PerspectiveCamera
  makeDefault
  position={[0, 3, 5]}
  fov={75}
  bind:ref={camera}
>
  <OrbitControls
    maxPolarAngle={degToRad(85)}
    minPolarAngle={degToRad(10)}
    enableDamping
    target={{ y: 0.5 }}
  />
</T.PerspectiveCamera>

<T.Group>
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
</T.Group>
