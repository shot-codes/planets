<script>
  import { Canvas } from "@threlte/core";
  import { World, Debug } from "@threlte/rapier";
  import Scene from "$lib/Scene.svelte";
  import { HTML } from "@threlte/extras";
</script>

<div>
  <Canvas>
    <World gravity={{ y: -10 }}>
      <Debug />
      <Scene />
      <HTML slot="fallback" transform>
        <p>No WASM? 😑</p>
      </HTML>
    </World>
  </Canvas>
</div>

<style>
  div {
    height: 100vh;
    width: 100vw;
  }
</style>
