
# data files

Supported in .md files or as .toml files

## improved multiline 

```
'''toml
@story
description = 
    this is multiline
    much easier
    no need to do quotes
name = ...
'''
```

will convert to proper multiline before using toml parser

## in .md files

```
'''toml
:mycircle/story
name = ...
description = 
'''
```

- story refers to the schema used (JSX schema) as defined in the mentioned circle
- mycircle refers to the circle as defined on local3bot

## how are schema's and 3bots defined


```
:mycircle/story
name = ...
description = 
```

means mycircle in local 3bot

or

```
:mycircle@kristof/story
name = ...
description = 
```

- means mycircle in remote 3bot with 3bot name ```kristof```

