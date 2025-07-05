<script lang="ts">
    let { children, class: className = "" } = $props();
</script>

<div class="[ flex flex-col min-w-[15%] justify-start ]
            [ bg-[#1e1e1e4b] ]
            [ text-white text-center ]
            {className}">
    {@render children()}
</div>