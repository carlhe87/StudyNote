---
tags:
  - Obsidian
---
# syntax: 
- `![[Note]]`
	- `![[Note#Heading]]`
	- `![[Note#^block]]`
# feature: 
- embedded content is displayed in sync with original 
	- original file can be accessed via link in embed
	- However, editing is only possible in original file, with following exception.
- Exception: embed can modify **Task**.Status!
	- e.g. can toggle click **task**.Status from hosting page
- embed capture **fold**.Status!
	- However, folding status is only a snapshot at time of embed, not updated if content is unchanged, i.e. change in **folding**.Status in is **not** in sync
- more capability: see Documentation
	- file: image, pdf, as attachment 
		- with parameter 
	- list: as block
	- query: as code block
# application
Generally, embed contains a link, and provide additional access to content, especially the capability to change task status. It enables outline style editing via add/remove `!` before the link. 
### use case 1: outline style editing
- generate a list of files via search query
- turn link into embed by (batch) adding `!` before link.
- adjust order of content by temporarily (batch) remove `!`
### use case 2: task tracking
- embed ToDo file original file
- update status from embed, without switching to original