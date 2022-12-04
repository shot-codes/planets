<script lang="ts">
  import type { Position } from "@threlte/core";
  import type { PlanetType } from "./Planet.svelte";
  import Planet from "./Planet.svelte";
  import PlanetGroupCore from "./PlanetGroupCore.svelte";

  export const position: Position | undefined = undefined;

  let planets: PlanetType[] = [
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
      position: { x: 30, y: 10, z: -30 },
    },
    {
      text: "there",
      position: { x: -30, y: -10, z: -30 },
    },
  ];
</script>

<PlanetGroupCore />

{#each planets as planet}
  <Planet
    bind:rigidBody={planet.rigidBody}
    text={planet.text}
    position={planet.position}
  />
{/each}
