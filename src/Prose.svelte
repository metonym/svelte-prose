<script>
  export let hideToc = false;
  export let toc = [];

  import { setContext } from "svelte";

  let headings = [];
  let current_index = -1;

  setContext("Prose", {
    add: item => {
      headings = [...headings, item];
    },
    remove: id => {
      headings = headings.filter(_ => _.id !== id);
    }
  });

  $: toc = headings
    .map(item => (item.tag === "h1" ? { ...item, children: [] } : item))
    .reduce((items, item, index) => {
      if (item.tag !== "h1") {
        items[current_index].children = [
          ...items[current_index].children,
          item
        ];

        return items;
      }

      current_index = index;

      return [...items, item];
    }, []);
</script>

<style>
  :global(.prose) {
    line-height: 1.42;
  }

  :global(.prose > h1, h2, h3, h4, h5) {
    line-height: 1.2;
    margin-top: 2rem;
    margin-bottom: 1rem;
  }

  :global(.prose > * + p) {
    margin-bottom: 1.5rem;
  }

  ul ul {
    padding-left: 2rem;
  }
</style>

<div class="prose" {...$$restProps}>
  {#if !hideToc}
    <nav>
      <h1 id="table-of-contents">Table of Contents</h1>
      <ul>
        {#each toc as { id, text, children }}
          <li>
            <a href="#{id}">{text}</a>
            <ul>
              {#each children as child}
                <li>
                  <a href="#{child.id}">{child.text}</a>
                </li>
              {/each}
            </ul>
          </li>
        {/each}
      </ul>
    </nav>
  {/if}

  <slot {toc} />
</div>
