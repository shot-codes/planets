<script lang="ts">
  import { T } from "@threlte/core";
  import { LayerMaterial, Fresnel } from "lamina/vanilla";
  import { Color } from "three";

  const laminaMaterial = new LayerMaterial({
    color: "#ffffff",
    lighting: "standard",
    layers: [
      new Fresnel({
        color: new Color("#b4baff"),
        alpha: 1,
        power: 1.5,
        intensity: 1.5,
        bias: 0,
        mode: "normal",
        visible: true,
      }),
    ],
  });
</script>

<T.Mesh material={laminaMaterial}>
  <T.SphereGeometry />
</T.Mesh>
