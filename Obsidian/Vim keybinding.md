---
tags:
  - vim
  - key-binding
  - Obsidian
---
# General
## mode
- `i` insert mode - text editor 
- `v` **visual** mode - select for next action (e.g. `y` `d` ) 
	- `V` visual **line** mode
	- `Ctrl+V` visual **block** mode (rectangle selection)
- `R` **Replace** mode
- `:` **command** mode
- `ESC` or `Ctrl+[` exit to normal mode
	- now mapped to `jj` for insert>>normal

## command mode
`:h` help
`:%s/foo/bar/g` to replace all ‘foo’ with ‘bar’
- `:` Enters command mode
- `%` Means across all lines
- `s` Means substitute
- `/foo` is regex to find things to replace
- `/bar/` is regex to replace things with
- `/g` means global, otherwise it would only execute once per line
## command syntax:
`action` + `number`+ `unit`   
- action e.g. `d` delete 
- (optional) repeat number  
- units e.g. `w` word  ## exit
## file //not in Obsidian
- `:!` run shell commands e.g.  `:!dir` or `:!ls`
- `:w - filename` save the file as "filename"
- `:r - filename` insert content to file "filename" #doubt
- `:wq` - or `:qw` or `:q` or `ZZ` to save and exit #doubt
- `:q!` - to trash all changes
- `ctrl-w`  jump window
- `:e` + `ctrl`+`d` list all command starts with :e
	- and press tab to complete the command
## undo redo
- `u` **undo** last command
	- `U` **undo** the whole line//not in Obsidian #doubt
- `CTRL-R` to **redo**
- `.` repeat last command
 
## Navigate
- `h`  /  `l`  left/right
	- `H` / `L`/ `M` top/bottom/middle of window
		- `zz`  focus window to center current line
- `j` / `k`  down/up
	- `J`  joint next line
- `w`  next **word**.start (word = string of purely a-z or 0-9)
	- `W`  (word = string divided by white space)
- `e`  forward word.**end**
	- `E`  (word = string divided by white space)
- `b`  backward word.**begin**
	- `B`  (word = string divided by white space)
- `0`  line.Begin
	- `^`  except white space
- `$`  line.End
- `%`  jump match pair `()` `{}` `[]` in line
- `zz` scroll current line at **center** of window
	- `zt` scroll current line at **top** of window
	- `zb` scroll current line at **bottom** of window
- `gg` - **go** to 1st line
- `G` - **go** to last line
	- `123`+`G` - go to line 123
- `fx` **find** forward to next "x" 
	- - `Fx` backward
- `tx` find forward **till** next "x" (offset 1 character) 
	- `Fx` `Tx`  **backward**
	- `;` **repeat** 
		- `,` in reverse direction 
- `{` `}` jump to previous/next  paragraph (empty line)
- `'`  jump to **mark**
- `x`+`j` go down x line
- `x`+`k` go up x line
## Edit
### Edit and remain in CommandMode
- `x`  **delete** 1 character
- `d`+  **delete** certain characters
	- `D`+  **delete** till Line.End 
	- `dw` word + white space (untill next word.Start)
		- `d2w`  2 words 
		- `diw`  "**in**" word under cursor
		- `daw`  "**around**" word under cursor and white space
	- `de` till word.**End** (keep white space)
	- `dd` line
		- `2dd`  2 lines
	- `dip` in paragraph(for Markdown, paragraph divided by empty line)
	- `dgg` from here up
		- `dG` from here down
	- `df2.` till 2nd "." (including ".")
	- `dt2.` untill 2nd "." (exluding ".")
	- `di(` inside ()
- `J` **join** next line (delete Line.End)
- `r`+`x` **replace** 1 character with "x" 
	- `R` Replace_mode, `ESC` to exit
- `y`  **copy** (selection) to clipboard
	- `yw` - word + whitespace
		- y2w - 2 words
	- `yy` or `Y` - 2 lines
- `p` **paste** after cursor 
	- `P`  **before**
	- `ap`  paste content in register 'a'
### Edit & enter InsertMode
- `i` **insert** at **cursor**.Start
	- `I` **line**.Start 
- `a` - **append** at **cursor**.End
	- `A` - at **line**.End 
- `o` - **open** new line below 
	- `O` - above
- `c`+ range:  **cut** (selection) to clipboard
	- `C`- **cut** (till line.End) 
	- `ce`- **cut** till word.End
	- `cw`- **cut** untill next word.Start
	- `cc`- **cut** entire line
- `s` **substitute** (selection) to clipboard
	- same as cut, but can only use alone, while c must use in combination of range
	- `S` operate on entire line
## search 
- search global
	- `/` backward 
		- `?` forward
	- `n`  find next 
		- `N`  find previous
- search in-line
	- `f`+`x` search in-line for x
## replace
- `:s/old/new/g` **substitute** 'new' for 'old' **globally**
- `%` find a matching use `) ] }` #doubt 
# mark  `'`
- `ma` **mark** line and register as 'a'
- `'a` **jump** to line registered as 'a'
- `''` **jump** back to previous position
# register  `"`
see `:h registers` for details
### unnamed 
- `""` last deleted by `d` `c` `s` `x` or copy by `y`
- `"0`... `"9` last 10 unnamed
- `"+` clipboard
### named `"a` `"b`...
### read-only
- `".` last inserted text
- `"%` current file path
- `":` most recent command
	- `@:`execute again in CommandMode  
- `"#` name of 'alternate file'
	- `:h alternate-file` for details
	- `:e Ctrl-r #` = `Ctrl-^` switch between files
### expression register// NA Obsidian
//unavailable in Obsidian
- `"=` result of expression
	- insertMode: `Ctrl-r` `=`, enter command line
		- type 2+2 enter --> print 4
### search register// NA Obsidian
//unavailable in Obsidian
- `*` or `#` last searched with `/` or `?`

# use with command
- `"ay` copy and add to register 'a'
- `"ap` paste content in regsiter 'a'
- in insert/command mode: `Ctrl-r`+ `a` 
- `:reg` check all register content
	- `:reg a` check register 'a' content
	- `:reg ""` check unnamed register  content
- `:let @+=@%` copy current file to clipboard
# macros
see `:h recording` for details
`qx` record macro 'x'
`@x` execute macro 'x'
`"x` macro register
- possible to edit macro register
	- `:let @W='i;` append command `i;` to macro 'w'
	- `:let @w='<Ctrl=r w>` change macro 'w'




---
tags: 
aliases:
---


# vim command
## not in Obsidian
`()`  `{}` move sentense/paragraph up/down 
`Ctrl+D/U` move up/down half page
`Ctrl+F/B` move up/down full page
## avail in Obsidian
`f` `F` jump forward/backward
`gg` `G` move to top/bottom of page
NumPad: `-` `+` move up/down
## enter/exit visual mode
`v` enter/exit `V` line 
normal mode use `Shift`+`directions`
back to normal mode: `Ctrl`+`C` or `Esc`
	additionally, 
		from visual mode: `v`
		from insert mode: `Ctrl`+`[`
### normal mode> insert mode
`i`/`a` before/after cursor, `o`/`O` line down/up
`ce` `cw` `ciw` `cc` select(e,w,iw,aw,line etc.) delete >insert
`s` :  delete >insert

`yy` `yi(` `ya(` copy line, in(), around ()
`dw` `ds` `dp`  delete word,sentence,paragraph
`df.` `dt.` delete till `.` until `.`

`/` `?` search forward `n` `N` next/previous
`*` `#` search current word and 
	focus forward to last/ backward to first

bookmark `m`+`x` tild + "x" goto book mark "x"
- [ ] integrate this into note [[Vim keybinding|Vim keybinding]]




