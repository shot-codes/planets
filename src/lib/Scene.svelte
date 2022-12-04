<script lang="ts">
  import type { PlanetType } from "./Planet.svelte";
  import { OrbitControls, T } from "@threlte/core";
  import { Environment } from "@threlte/extras";
  import PlanetGroup from "$lib/PlanetGroup.svelte";

  let planetGroup1: PlanetType[] = [
    {
      text: "hello",
      position: { x: -30, y: 10, z: 30 },
    },
    {
      text: "there",
      position: { x: 30, y: -10, z: 30 },
    },
    {
      text: "hello",
      position: { x: -28, y: 10, z: -30 },
    },
    {
      text: "there",
      position: { x: -30, y: -10, z: -30 },
    },
  ];

  let planetGroup2: PlanetType[] = [
    {
      text: "hello",
      position: { x: -30, y: 10, z: 30 },
    },
    {
      text: "there",
      position: { x: 30, y: -10, z: 30 },
    },
    {
      text: "hello",
      position: { x: -28, y: 10, z: -30 },
    },
    {
      text: "there",
      position: { x: -30, y: -10, z: -30 },
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
