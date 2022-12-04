<script lang="ts">
  import type { Position, Rotation } from "@threlte/core";
  import { T } from "@threlte/core";
  import { RigidBody, Collider } from "@threlte/rapier";
  import type { RigidBody as RapierRigidBody } from "@dimforge/rapier3d-compat";
  import { LayerMaterial, Fresnel } from "lamina/vanilla";
  import { Color } from "three";

  export let position: Position | undefined = undefined;
  export let rotation: Rotation | undefined = undefined;
  export let rigidBody: RapierRigidBody | undefined = undefined;

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

<RigidBody
  bind:rigidBody
  type={"dynamic"}
  {position}
  {rotation}
  linearDamping={2}
>
  <T.Group>
    <T.Mesh material={laminaMaterial}>
      <T.SphereGeometry />
      <Collider
        contactForceEventThreshold={30}
        restitution={0.4}
        shape={"ball"}
        args={[1]}
      />
    </T.Mesh>
  </T.Group>
</RigidBody>
