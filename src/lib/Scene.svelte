<script lang="ts">
  import { OrbitControls, T } from "@threlte/core";
  import { Environment } from "@threlte/extras";
  import PlanetGroup from "$lib/PlanetGroup.svelte";
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

<PlanetGroup />
