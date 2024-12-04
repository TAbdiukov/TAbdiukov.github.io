# TAbdiukov.github.io
Website!

## How to build and run

### git

clone,
```
git clone --recurse-submodules -j8 git://github.com/foo/bar.git
cd bar
```

update submodules,
```
git submodule update --remote --merge
```

### Hugo

build,

```
hugo --gc --minify -D --theme=hugo-vitae-nord
```

run,

```
hugo server -D -F --theme=hugo-vitae-nord
```

### Displaying drafts and future articles

- use the `-D` option for drafts
- use the `-F` option for content with `date` in the future
