<script lang="ts">
  import type { PlanetType } from "./Planet.svelte";
  import { OrbitControls, T } from "@threlte/core";
  import { Environment } from "@threlte/extras";
  import PlanetGroup from "$lib/PlanetGroup.svelte";

  let planetGroup1: PlanetType[] = [
    {
      text: "1",
      position: { x: 103, y: 103, z: 103 },
    },
    {
      text: "2",
      position: { x: 97, y: 97, z: 97 },
    },
    {
      text: "3",
      position: { x: 100, y: 100, z: 100 },
    },
    {
      text: "4",
      position: { x: 100, y: 100, z: 100 },
    },
  ];

  let planetGroup2: PlanetType[] = [
    {
      text: "10",
      position: { x: 100, y: 100, z: 100 },
    },
    {
      text: "20",
      position: { x: 100, y: 100, z: 100 },
    },
    {
      text: "30",
      position: { x: 100, y: 100, z: 100 },
    },
    {
      text: "40",
      position: { x: 100, y: 100, z: 100 },
    },
  ];
</script>

<Environment
  path="/"
  files="nebula_low_res.hdr"
  isBackground={true}
  format="hdr"
/>

<T.AmbientLight intensity={0.15} />

<T.PerspectiveCamera makeDefault position={[0, 3, 40]} fov={90}>
  <OrbitControls enableDamping target={{ y: 0.5 }} />
</T.PerspectiveCamera>

<PlanetGroup planets={planetGroup1} position={[0, 0, 0]} />

<!-- <PlanetGroup planets={planetGroup2} position={[100, 100, 100]} /> -->
