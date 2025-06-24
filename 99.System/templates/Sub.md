---
type: sub
tags:
  - sub
date: "{{date}}"
size:
---
# Игры
```dataview
table without id 
    inlink as имяФайла,
    inlink.file.day as датыИгр
from "02.Ervindell/99.System/Subs"
where file.name="{{title}}"
flatten file.inlinks as inlink
sort inlink.file.name
```
