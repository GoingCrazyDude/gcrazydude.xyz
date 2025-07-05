<script lang="ts">
    let { children } = $props();
</script>

<div class="[ flex min-w-[80%] min-h-[90%] m-4 backdrop-blur-2xl ]
			[ rounded-xl border-2 bg-black/25 border-[#171616]/35 shadow-xl/50 overflow-hidden ]
            [ text-white ]
            [ before:absolute before:inset-0 before:bg-[url(/media/Noise.png)] before:bg-repeat before:opacity-45 before:-z-10 ]">
    {@render children()}
</div>