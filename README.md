# svelte-prose

[![NPM][npm]][npm-url]
[![Build][build]][build-badge]

> Typography utilities for Svelte.

Inspired by the U.S. Web Design System [Prose component](https://designsystem.digital.gov/components/typography/#prose), `svelte-prose` is a collection of components for long-form typography.

## Install

```bash
yarn add -D svelte-prose
```

## Usage

```html
<script>
  import Prose, { T } from "svelte-prose";
</script>

<Prose>
  <T.H1 text="Heading level 1" />
  <T.H2 text="Heading level 2" />
  <p>Some text content.</p>
</Prose>
```

### Headings

A Heading component (`T.H1`, `T.H2`, `T.H3`, `T.H4`, `T.H5`, `T.H6`) automatically creates an id from the text prop.

```html
<T.H1 text="Heading level 1" />
<!-- <h1 id="heading-level-1">Heading level 1</h1> -->
```

### Table of Contents

The `Prose` component creates a two-tiered table of contents from headings.

Hide the default ToC to render your own:

```html
<Prose hideToc let:toc>
  <nav>
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
  <T.H1 text="Heading level 1" />
  <T.H2 text="Heading level 2" />
  <p>Some text content.</p>
</Prose>
```

## API

### `Prose`

| Property name | Value                                                                 |
| :------------ | :-------------------------------------------------------------------- |
| hideToc       | `boolean` (default: `false`)                                          |
| toc           | `[]{ id: string; text: string; tag: 'h1' | string; }` (default: `[]`) |

### `T.H{1-6}`

| Property name | Value                           |
| :------------ | :------------------------------ |
| text          | `string` (default: `undefined`) |

#### Forwarded events

- on:click
- on:mouseover
- on:mouseenter
- on:mouseout

## [Changelog](CHANGELOG.md)

## License

[MIT](LICENSE)

[npm]: https://img.shields.io/npm/v/svelte-prose.svg?color=blue
[npm-url]: https://npmjs.com/package/svelte-prose
[build]: https://travis-ci.com/metonym/svelte-prose.svg?branch=master
[build-badge]: https://travis-ci.com/metonym/svelte-prose
