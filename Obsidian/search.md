---
tags: Obsidian
---


# search and query
## call search function
- see [help](https://help.obsidian.md/Plugins/Search)
- keywords: select text and `ctrl`+`shift+F`
- recent query: leave search term empty
- default scope: only **notes**,  expand scope to **path** or **file**, use `path:` or `file:`
- Copy search results: three dots
- Change result order: Aa

### search syntax
- exact phrase use `""`
	- use `\"` to escape `"`
- default imply `AND`, specify `OR`  if needed
- use `-` to indicate `NOT`
- use `()`
- regex: `/` ...`/`
	- JavaScript-flavored [regex](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)
### search operator
`file:` in file name. Scope: any file
`path:` in file path. Scope: any file
`content:` in content
`tag:` in tags
- scope: ignores code blocks or non-Markdown content, thus faster

`match-case:` Case-sensitive
- or click **Match case** ("Aa" icon) inside the search bar.
`ignore-case:` case insensitive: (by default)

`line:` in same line
- Example: `line:(mix flour)`
`block:` in same block
- require parse in file, thus slower
`section:` in same section: (between 2 headings)

`task:` in task, block-by-block
	`task-todo:` uncompleted
	`task-done:` completed

`[property]` return files with certain 'property':
- `[property:value]` to return files with that property and value:
- `[aliases]` returns files that contain the `aliases` property
	- `[aliases:Name]` returns files where the `aliases` property value is `Name`
## Embed search results in a note
 `query` code block:
````
```query
embed OR search
```
````