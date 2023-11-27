With Hugo:

build:

```bash
hugo --gc --minify -D --theme=hugo-vitae-nord -b http://open.id.au/
```

run:

```bash
hugo server -D -F --theme=hugo-vitae-nord
```

### Displaying drafts and future articles

- use the `-D` option for drafts
- use the `-F` option for content with `date` in the future
