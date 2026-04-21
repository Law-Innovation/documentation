# Writing Guide

Everything you need to know to edit or add content to the Consenter documentation. You do not need any coding experience to get started.

## How content is organized

All documentation lives in the `docs/` directory as `.mdx` files. The URL of each page is determined by its file path. For example, `docs/getting-started/purposes.mdx` becomes `/getting-started/purposes` on the site.

A few things worth knowing about file naming:

- A file named `index.mdx` inside a folder maps to the folder root (so `docs/getting-started/index.mdx` becomes `/getting-started`)
- Each folder can include a `meta.json` file to control the display name and order of pages in the sidebar
- Two files should never resolve to the same URL

More details in the [Fumadocs page conventions reference](https://www.fumadocs.dev/docs/page-conventions).

## Writing MDX

MDX is standard Markdown with support for components. If this is your first time using Markdown, it is a simple way to format text using plain characters — think headings with `#`, bold with `**`, and links with `[text](url)`. The [Fumadocs markdown reference](https://www.fumadocs.dev/docs/markdown) covers the full syntax.

### Frontmatter

Every page must begin with a frontmatter block. This is a short section at the very top of the file wrapped in `---` that tells the site the page title and other metadata.

```mdx
---
title: My Page Title
---
```

The `title` field is required. It becomes the main heading displayed at the top of the page, so you do not need to add a separate `# H1` heading in the body.

### Built-in components

Fumadocs ships with components you can drop into any MDX file without importing anything.

**Callout** highlights important information:

```mdx
<Callout type="info">This is something the reader should know.</Callout>
```

The `type` can be `info`, `warn`, `error`, `success`, or `idea`.

**Cards** create a grid of navigation links:

```mdx
<Cards>
  <Card
    href="/getting-started/purposes"
    title="Consenter Purposes"
    description="What you can ask users for."
  />
</Cards>
```

**Steps** are useful for sequential guides:

```mdx
<Steps>
  <Step>First, do this.</Step>
  <Step>Then, do that.</Step>
</Steps>
```

### Code blocks

Wrap code in triple backticks and specify the language for syntax highlighting:

````mdx
```js
console.log("hello world");
```
````

### Links

Internal links use standard Markdown syntax and are automatically optimized by the framework. External links get security attributes added automatically.

```mdx
[Go to purposes](/getting-started/purposes)
[Fumadocs](https://fumadocs.dev)
```

## Resources

- [Fumadocs Markdown Reference](https://www.fumadocs.dev/docs/markdown)
- [Page and File Conventions](https://www.fumadocs.dev/docs/page-conventions)
