<script lang="ts">
    import { marked } from 'marked';
    import { onMount, tick, type Snippet } from 'svelte';
    
    interface Props {
        children?: Snippet;
        source?: string;
        class?: string;
    }

    let { children, source, class: className = "" }: Props = $props();
    let markdownSource: string = source || '';
    let renderedHtml: string = $state('');
    let hiddenContainer: HTMLDivElement | undefined = $state();
    
    marked.setOptions({
        breaks: true,
        gfm: true,
        async: false,
    });
    
    function renderMarkdown(markdown: string): void {
        if (markdown) {
            renderedHtml = marked.parse(markdown) as string;
        }
    }
    
    onMount(async (): Promise<void> => {
        if (!source && children && hiddenContainer) {
            // wait for the DOM to update
            await tick();
            
            // extract text content from the hidden container
            const textContent: string = hiddenContainer.textContent || hiddenContainer.innerText || '';
            
            // clean up the markdown text
            markdownSource = textContent
                .trim()
                .split('\n')
                .map((line: string) => line.trim())
                .join('\n')
                .replace(/\n\s*\n/g, '\n\n'); // normalize double line breaks
        }
        
        // render markdown to html
        renderMarkdown(markdownSource);
    });
    
    // reactive statement to re-render when source changes
    $effect(() => {
        renderMarkdown(markdownSource);
    });
</script>

<!-- if using children, render them hidden first to extract text -->
{#if !source && children}
    <div bind:this={hiddenContainer} style="position: absolute; left: -9999px; visibility: hidden; white-space: pre;">
        {@render children()}
    </div>
{/if}

<!-- render the actual markdown -->
<div class="markdown-content flex flex-col {className}">
    {@html renderedHtml}
</div>

<style>
    .markdown-content :global(h1) {
        text-shadow: #f0d48e 0px 0px 10px;
        color: #e7b435;
        font-size: 2rem;
        font-weight: bold;
        line-height: 1.2;
        margin-bottom: 1rem;
    }
    
    .markdown-content :global(h2) {
        text-shadow: #f0d48e 0px 0px 5px;
        color: #f3c95f;
        font-size: 1.5rem;
        font-weight: bold;
        line-height: 1.3;
        margin-bottom: 0.75rem;
    }
    
    .markdown-content :global(h3) {
        text-shadow: #f0d48e 0px 0px 2.5px;
        color: #f8da8f;
        font-size: 1.25rem;
        font-weight: bold;
        line-height: 1.4;
        margin-bottom: 0.5rem;
    }
    
    .markdown-content :global(p) {
        line-height: 1.6;
    }
    
    .markdown-content :global(ul), .markdown-content :global(ol) {
        margin-bottom: 0.5rem;
        padding-left: 1.5rem;
    }
    
    .markdown-content :global(li) {
        list-style: disc;
        margin-bottom: 0.25rem;
    }
    
    .markdown-content :global(strong) {
        font-weight: 800;
        text-shadow: #e7b435 0 0 10px;
    }
    
    .markdown-content :global(em) {
        font-style: italic;
    }
    
    .markdown-content :global(code) {
        background-color: #f3f4f6;
        padding: 0.125rem 0.25rem;
        border-radius: 0.25rem;
        font-family: monospace;
        font-size: 16px;
    }
    
    .markdown-content :global(pre) {
        display: flex;
        max-width: 75%;
        padding: 1rem;
        background-color: #000000;
        border-radius: 0.5rem;
        margin-top: 1rem;
        margin-bottom: 1rem;
    }
    
    .markdown-content :global(pre code) {
        background-color: transparent;
        padding: 0;
    }

    .markdown-content :global(a) {
        transition-duration: 200ms;
        color: #e7b435;
        text-decoration: underline;
    }

    .markdown-content :global(a):hover {
        color: #f0d48e;
    }
</style>