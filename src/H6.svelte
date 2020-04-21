<script>
  export let text = undefined;

  import Heading from "./Heading.svelte";
</script>

<Heading {...$$restProps} tag="h6" {text} />
