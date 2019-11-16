
# Specs for wiki processing

## process links

- [links](../docs/wiki/links.md)
- need to check if the link exist if --check is given to 3git

## process includes

- [includes](../docs/wiki/macros/include.md)
- basics
    - include other docs in full from remote git repo's
    - include into local repo
- full functionality should only be here later (**) start with basics

## macros

### gpdf 

- [gpdf](../docs/wiki/macros/gpdf.md)
- if too complicated in crystal use connection to localhost actor on 3bot server

### dynamic content from actors

- [dynamic content](../docs/wiki/macros/dynamic_content.md)

### process graphiz markup

- [dot macro usage](../docs/wiki/macros/dot.md)
- output png which is put in same dir
- if png >100kb then will be processed with how to deal with files functionality

### gallery (**)

- [gallery](../docs/wiki/macros/gallery.md)
- the links are checked and files > 100kb will be moved to filedir

### team (**)

- [team](../docs/wiki/macros/team.md)

### slideshow (**)

- [gpdf](../docs/wiki/macros/slideshow.md)

