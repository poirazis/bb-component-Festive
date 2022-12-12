<script>
  import { getContext } from "svelte"
  import { Confetti } from 'svelte-confetti'
  import ToggleConfetti from "./ToggleConfetti.svelte";

  export let text

  const { styleable } = getContext("sdk")
  const component = getContext("component")
</script>

<div use:styleable={$component.styles}>
  <ToggleConfetti toggleOnce relative={false}>
	
	<div style="position: fixed; top: -50px; left: 0; height: 100vh; width: 100vw; display: flex; justify-content: center; overflow: hidden;">
		<Confetti x={[-5, 5]} y={[0, 0.1]} delay={[500, 2000]}  infinite duration=5000 amount=400 fallDistance="100vh" />
	</div>
</ToggleConfetti>
</div>
