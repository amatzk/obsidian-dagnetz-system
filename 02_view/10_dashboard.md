---
tags:
  - dashboard
---
## Task
```base
views:
  - type: table
    name: imcomplete
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
formulas:
  note_title: file.asLink(file.name.replace(/^\d{4}-\d{2}-\d{2}_|_\d{4}-\d{2}-\d{2}$/, ""))
views:
  - type: table
    name: pin
    filters:
      and:
        - file.path.contains("01_data")
        - file.hasTag("Pin")
    order:
      - file.tags
      - formula.note_title
    sort:
      - property: file.mtime
        direction: DESC
```

## Today
```base
formulas:
  backlinks: file.backlinks.map(if(value.asFile(), value.asFile().asLink(value.asFile().name.replace(/\.[^\.]+$/, "")), null)).unique().filter(value)
  last_edit: file.mtime.relative()
  note_title: file.asLink(file.name.replace(/^\d{4}-\d{2}-\d{2}_|_\d{4}-\d{2}-\d{2}$/, ""))
properties:
  formula.backlinks:
    displayName: backlinks
  formula.last_edit:
    displayName: last edit
views:
  - type: table
    name: today
    filters:
      and:
        - file.inFolder("01_data/" + today().format("YYYY/MM/DD"))
        - '!file.hasTag("task")'
    order:
      - file.tags
      - formula.note_title
    sort:
      - property: file.mtime
        direction: DESC
```

## Data
```base
formulas:
  backlinks: file.backlinks.map(if(value.asFile(), value.asFile().asLink(value.asFile().name.replace(/\.[^\.]+$/, "")), null)).unique().filter(value)
  note_title: file.asLink(file.name.replace(/^\d{4}-\d{2}-\d{2}_|_\d{4}-\d{2}-\d{2}$/, ""))
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
    order:
      - file.tags
      - formula.note_title
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
      - formula.note_title
    sort:
      - property: file.mtime
        direction: DESC
  - type: table
    name: notes
    filters:
      and:
        - file.folder.contains("01_data")
        - file.ext == "md"
    order:
      - file.tags
      - formula.note_title
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
