<script>
  export let tag = "h1";
  export let text = "Heading " + tag;

  import { getContext, onMount } from "svelte";

  const ctx = getContext("Prose");

  onMount(() => {
    if (ctx) {
      ctx.add({ id, text, tag });
    }

    return () => {
      if (ctx) {
        ctx.remove(id);
      }
    };
  });

  $: id = text.replace(/\s+/g, "-").toLowerCase();
</script>

{#if tag === 'h1'}
  <h1 {...$$restProps} {id} on:click on:mouseover on:mouseenter on:mouseout>
    {text}
  </h1>
{:else if tag === 'h2'}
  <h2 {...$$restProps} {id} on:click on:mouseover on:mouseenter on:mouseout>
    {text}
  </h2>
{:else if tag === 'h3'}
  <h3 {...$$restProps} {id} on:click on:mouseover on:mouseenter on:mouseout>
    {text}
  </h3>
{:else if tag === 'h4'}
  <h4 {...$$restProps} {id} on:click on:mouseover on:mouseenter on:mouseout>
    {text}
  </h4>
{:else if tag === 'h5'}
  <h5 {...$$restProps} {id} on:click on:mouseover on:mouseenter on:mouseout>
    {text}
  </h5>
{:else if tag === 'h6'}
  <h6 {...$$restProps} {id} on:click on:mouseover on:mouseenter on:mouseout>
    {text}
  </h6>
{/if}
