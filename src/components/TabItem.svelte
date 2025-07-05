<script lang="ts">
    let { children, class: tailwindClass = "", href: ref = "" } = $props();
</script>

<div class="{tailwindClass} hover:bg-black/45 m-1 py-1.5 hover:rounded-md duration-100">
    <a href={ref}>
        {@render children()}
    </a>
</div>