<script>
</script>

<div class="@container text-center overflow-hidden">
	<h1 class="text-4xl md:text-5xl"><span class="hover:opacity-5">Shy Bridge</span></h1>
	<div class="@container/full-bridge min-w-full flex flex-row" id="shy-bridge">
		<img alt="Shy Bridge" class="mx-auto my-8 w-1/2 max-h-1/2" id="shy-bridge-half-1"
		     src="/images/bridge-half-1.webp">
		<h2 class="text-4xl text-red-400" id="shy-text">I'm too shy sorry ~ :3</h2>
		<img alt="Shy Bridge" class="mx-auto my-8 w-1/2 max-h-1/2" id="shy-bridge-half-2"
		     src="/images/bridge-half-2.webp">
	</div>
	<p class="text-lg md:text-xl">A bridge that is too shy to show itself.</p>
</div>
<style>
	#shy-bridge #shy-bridge-half-1,
	#shy-bridge #shy-bridge-half-2 {
		transition: transform 1s ease-in-out;
	}

	#shy-bridge {
		position: relative;
	}

	#shy-bridge #shy-text {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		opacity: 0;
		transition: opacity 1s ease;
	}

	#shy-bridge:hover #shy-text {
		opacity: 1;
	}

	#shy-bridge:hover #shy-bridge-half-1 {
		transform: translateX(-100%);
	}

	#shy-bridge:hover #shy-bridge-half-2 {
		transform: translateX(100%);
	}
</style>