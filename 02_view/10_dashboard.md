---
tags:
  - dashboard
---
## Task
```base
views:
  - type: table
    name: incomplete
    filters:
      and:
        - file.path.contains("01_data")
        - file.hasTag("task")
        - complete == false
    order:
      - complete
      - file.tags
      - file.name
    sort:
      - property: file.mtime
        direction: DESC
  - type: table
    name: complete
    filters:
      and:
        - file.path.contains("01_data")
        - file.hasTag("task")
        - complete == true
    order:
      - complete
      - file.tags
      - file.name
  - type: table
    name: all
    filters:
      and:
        - file.path.contains("01_data")
        - file.hasTag("task")
    order:
      - complete
      - file.tags
      - file.name
```

## Pin
```base
views:
  - type: table
    name: pin
    filters:
      and:
        - file.path.contains("01_data")
        - file.hasTag("pin")
    order:
      - file.tags
      - file.name
    sort:
      - property: file.name
        direction: ASC
      - property: file.mtime
        direction: DESC

```

## Today
```base
formulas:
  backlinks: file.backlinks.map(if(value.asFile(), value.asFile().asLink(value.asFile().name.replace(/\.[^\.]+$/, "")), null)).unique().filter(value)
properties:
  formula.backlinks:
    displayName: backlinks
views:
  - type: table
    name: today
    filters:
      and:
        - file.inFolder("01_data/" + today().format("YYYY/MM/DD"))
        - '!file.hasTag("task")'
    order:
      - file.tags
      - file.name
    sort:
      - property: file.mtime
        direction: DESC

```

## Data
```base
formulas:
  backlinks: file.backlinks.map(if(value.asFile(), value.asFile().asLink(value.asFile().name.replace(/\.[^\.]+$/, "")), null)).unique().filter(value)
properties:
  formula.backlinks:
    displayName: backlinks
views:
  - type: table
    name: past
    filters:
      and:
        - file.folder.contains("01_data")
        - '!file.inFolder("01_data/" + today().format("YYYY/MM/DD"))'
        - '!file.hasTag("task")'
    order:
      - file.tags
      - file.name
    sort:
      - property: file.mtime
        direction: DESC
  - type: table
    name: all
    filters:
      and:
        - file.folder.contains("01_data")
        - '!file.hasTag("task")'
    order:
      - file.tags
      - file.name
    sort:
      - property: file.mtime
        direction: DESC
  - type: table
    name: notes
    filters:
      and:
        - file.folder.contains("01_data")
        - file.ext == "md"
        - '!file.hasTag("task")'
    order:
      - file.tags
      - file.name
    sort:
      - property: file.mtime
        direction: DESC
  - type: table
    name: assets
    filters:
      and:
        - file.folder.contains("01_data")
        - file.ext != "md"
    order:
      - file.ext
      - file.name
      - formula.backlinks
    sort:
      - property: file.mtime
        direction: DESC

```
