<script>
	import { onDestroy } from "svelte";
	import { ArrowRight, ArrowLeft, ArrowDown } from "@lucide/svelte";
	import Typewriter from "svelte-typewriter";

	let hovered = $state(false);
	let showCensored = $state(false);
	let timeoutId = null;

	function handleMouseEnter() {
		hovered = true;
		showCensored = false; // hide immediately on hover
		if (timeoutId) {
			clearTimeout(timeoutId);
			timeoutId = null;
		}
	}

	function handleMouseLeave() {
		hovered = false;
		if (timeoutId) clearTimeout(timeoutId);
		timeoutId = setTimeout(() => {
			if (!hovered) {
				showCensored = true; // show after 5s of no hover
			}
		}, 5000);
	}

	onDestroy(() => {
		if (timeoutId) clearTimeout(timeoutId);
	});
</script>

<div class="@container overflow-hidden text-center">
	<Typewriter>
		<h1 class="text-4xl md:text-5xl"><span class="hover:opacity-5">Shy Bridge</span></h1>
	</Typewriter>
	<div
		class="@container/shy-bridge flex min-w-full flex-row"
		id="shy-bridge"
		onmouseenter={handleMouseEnter}
		onmouseleave={handleMouseLeave}
		role="region"
	>
		<button
			id="arrow-left"
			aria-label="Go to scene 99"
			title="Go to scene 99"
			class="rounded-xl bg-yellow-500 px-5 py-10 hover:scale-[1.03] hover:bg-yellow-600 hover:shadow-2xl"
			onclick={() => {
				window.location.href = "/scenes/99";
			}}
		>
			<ArrowLeft />
		</button>
		<img
			alt="Shy Bridge"
			class="mx-auto max-h-1/3 w-1/2"
			id="shy-bridge-half-1"
			src="/images/bridge-half-1.webp"
		/>
		<h2 class="text-4xl text-red-400" id="shy-text">I'm too shy sorry ~ :(</h2>
		<img
			id="censored"
			src="/images/censored.webp"
			alt="censored"
			title="I'm too shy to be in front of you!"
			class="mx-auto my-8 max-h-1/2 w-1/2"
			style:opacity={showCensored ? 1 : 0}
		/>
		<img
			alt="Shy Bridge"
			class="mx-auto max-h-1/3 w-1/2"
			id="shy-bridge-half-2"
			src="/images/bridge-half-2.webp"
		/>
		<button
			id="arrow-right"
			aria-label="Go to scene 92"
			title="Go to scene 92"
			class="rounded-xl bg-amber-500 px-5 py-10 hover:scale-[1.03] hover:bg-amber-600 hover:shadow-2xl"
			onclick={() => {
				window.location.href = "/scenes/92";
			}}
		>
			<ArrowRight />
		</button>
	</div>

	<div id="arrow-down" class="flex min-w-full items-center justify-center text-center">
		<ArrowDown class="animate-bounce" size="50" />
	</div>

	<section id="lore">
		<Typewriter delay="2000" mode="cascade">
			<p class="m-2 text-2xl md:text-3xl">A bridge that is too shy to show itself.</p>
			<p class="m-2 text-2xl md:text-3xl">Unfortunately it doesn't have much self-confidence</p>
			<p class="m-2 text-2xl md:text-3xl">
				It actually used to be most confident bridge in the world - always staying available, night
				or day, rain or sun.
			</p>
			<p class="m-2 text-2xl md:text-3xl">
				But one day, it rained a lot, the river flooded, and the bridge couldn't open, it was stuck
				from not moving.
			</p>
			<p class="m-2 text-2xl md:text-3xl">
				All the other bridges laughed at it, as it got submerged, unable to do anything.
			</p>
			<p class="m-2 text-2xl md:text-3xl">Ever since, it has never been the same</p>
		</Typewriter>
	</section>
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

	#shy-bridge #arrow-left {
		position: absolute;
		top: 50%;
		left: 10%;
		transform: translate(-50%, -50%);
		opacity: 0;
		transition: opacity 0.5s ease;
	}

	#shy-bridge #arrow-right {
		position: absolute;
		top: 50%;
		left: 90%;
		transform: translate(-50%, -50%);
		opacity: 0;
		transition: opacity 0.5s ease;
	}

	#censored {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		transition: opacity 0.3s ease;
	}

	#shy-bridge:hover #shy-text {
		opacity: 1;
	}

	#shy-bridge:hover #arrow-right {
		opacity: 1;
	}

	#shy-bridge:hover #arrow-left {
		opacity: 1;
	}

	#shy-bridge:hover #shy-bridge-half-1 {
		transform: translateX(-100%);
	}

	#shy-bridge:hover #shy-bridge-half-2 {
		transform: translateX(100%);
	}
</style>
