<script>
  import { Canvas } from "@threlte/core";
  import { World } from "@threlte/rapier";
  import { spring } from "svelte/motion";
  import Scene from "$lib/Scene.svelte";
  import { HTML } from "@threlte/extras";

  const scale = spring(1);
</script>

<div>
  <Canvas>
    <World>
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
