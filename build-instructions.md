With Hugo:

build:

```
hugo --gc --minify -D --theme=hugo-vitae-nord -b http://open.id.au/
```

run:

```
hugo server -D -F --theme=hugo-vitae-nord
```

### Displaying drafts and future articles

- use the `-D` option for drafts
- use the `-F` option for content with `date` in the future
