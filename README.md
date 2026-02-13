# Vim University

Despite its reputation for minimalism, Vim has a surprising depth that rewards study. Here we list many of its most loved features, some tips, and a list of ideas for things to study or practice to take your Vim usage to the next level.

## Where to get help

- `:h` (`:help!`)
- `:h tutor`

## Laying out your workspace

- Splits:
  - `:sp`
  - `:vs`
  - `:on`
  - `CTRL-W {H,J,K,L}` move window to edge.
  - `CTRL-W r` rotate windows.
  - `CTRL-W _` maximize current window (vertically); count to size to specific height `10 CTRL-W _`.
  - `CTRL-W |` maximize current window (horizontally).
  - `CTRL-W =` equalize window sizes (vertically and horizontally).
  - `CTRL-W t` jump to topmost window.
  - `CTRL-W b` jump to bottommost window.
  - [Common re-mappings](https://github.com/wincent/wincent/blob/b94dafbe4caefa76305e90a37ad9342264fff5af/aspects/nvim/files/.config/nvim/plugin/mappings/normal.lua#L39-L42):
    - `CTRL-h` → `CTRL-W h` to focus window on left.
    - `CTRL-j` → `CTRL-W j` to focus window below.
    - `CTRL-k` → `CTRL-W k` to focus window above.
    - `CTRL-l` → `CTRL-W l` to focus window on right.
- Tabs
  - `:tabe`
  - `CTRL-W T`
  - `gt`/`gT` next/previous
  - `{count}gt` jump to `{count}` indexed tab
- tmux:
  - Splits (panes)
  - Windows
  - Sessions
- Foreground/backgrounding (`CTRL-Z`) vs `:terminal`
- Folds
  - `zm`: increase fold level (mnemonic: "more").
  - `zM`: increase fold level to maximum.
  - `zr`: reduce fold level (mnemonic: "reduce").
  - `zR`: reduce fold level to minimum.
  - `zc`: close fold, `zC` close folds recursively.
  - `zo`: open fold, `zO` open folds recursively.
  - `za`: toggle fold (Pro-tip™️: `<Tab>` is a good for [mapping to this](https://github.com/wincent/wincent/blob/b94dafbe4caefa76305e90a37ad9342264fff5af/aspects/nvim/files/.config/nvim/plugin/mappings/normal.lua#L9-L10)).
  - `zA`: toggle fold recursively.
  - `zv`: unfold folds to view cursor line (mnemonic: "view").
  - `:set foldlevelstart=1` (start with everything folded, `99` = start with nothing folded).
  - `:set foldmethod=indent` vs `marker` (eg. [`~/.config/nvim/init.lua`](https://github.com/wincent/wincent/blob/b94dafbe4caefa76305e90a37ad9342264fff5af/aspects/nvim/files/.config/nvim/init.lua#L471)).

## Navigation

- Movements/motions:
  - `H`, `M`, `L` move cursor to high, middle, low positions.
  - `CTRL-F` forward full screen, `CTRL-B` backward full screen.
  - `CTRL-D` down half screen, `CTRL-U` up half screen.
  - `{`, `}` move to previous/next blank line.
  - `gg` jump to top of buffer, `G` jump to bottom of buffer.
  - `%` jump to matching brace.
  - Relative line numbers:
    - `:set number`
    - `:set relativenumber`
    - `{count}j`: move down `{count}` lines
    - `{count}k`: move up `{count}` lines
  - Absolute line numbers:
    - `{count}G`: go to line `{count}`
    - `:[range]`: go to line `[range]` (eg. `:50`)
- Scrolling:
  - `CTRL-E` scroll up by one line, `CTRL-Y` scroll down by one line (cursor stays).
  - `zz` center current cursor line in viewport.
  - `zt` scroll current cursor line to top of viewport.
  - `zb` scroll current cursor line to bottom of viewport.
- Fuzzy finders:
  - https://github.com/nvim-telescope/telescope.nvim
  - https://github.com/wincent/command-t
- NvimTree: https://github.com/kyazdani42/nvim-tree.lua
  - `<LocalLeader>f`: To reveal in tree.
- vim-vinegar: https://github.com/tpope/vim-vinegar
- vim-dirvish: https://github.com/justinmk/vim-dirvish
- vim-projectionist: https://github.com/tpope/vim-projectionist
  - `:A` go to alternate file
  - `:AS` open alternate in split
  - `:AV` open alternate in a horizontal split
  - Sample configurations: [`~/.config/nvim/after/plugin/projectionist.lua`](https://github.com/wincent/wincent/blob/b94dafbe4caefa76305e90a37ad9342264fff5af/aspects/nvim/files/.config/nvim/after/plugin/projectionist.lua)
- LSP-powered navigation
  - Example project: [`~/code/masochist/next`](https://github.com/wincent/masochist/tree/next)
  - Go-to-definition, hover, autocomplete, inline diagnostics.
- Search-based navigation
  - Quickfix list
    - `:cn`
    - `:cp`
    - `:cnf`
    - `:cpf`
    - `:colder`
    - `:cnewer`
    - Pro-tip™️: `<Up>`, `<Down>`, `<Left>`, `<Right>` are good for mapping to these.
  - Location list:
    - `:lne`
    - `:lp`
    - `:lnf`
    - `:lpf`
    - `:lolder`
    - `:lnewer`
  - Plug-ins:
    - Ferret: https://github.com/wincent/ferret
    - vcs-jump: https://github.com/wincent/vcs-jump
- Within-file find-and-replace:
  - `:%s/`
  - Scalpel: https://github.com/wincent/scalpel
- Jump list:
  - `:jumps`
  - `CTRL-o`, `CTRL-i`/`<Tab>`
  - Filewise jumplist mappings: [`~/.config/nvim/plugin/mappings/leader.lua`](https://github.com/wincent/wincent/blob/b94dafbe4caefa76305e90a37ad9342264fff5af/aspects/nvim/files/.config/nvim/plugin/mappings/leader.lua#L47-L49).
  - Mappings to store big jumps in jump list: [`~/.config/nvim/plugin/mappings/normal.lua`](https://github.com/wincent/wincent/blob/b94dafbe4caefa76305e90a37ad9342264fff5af/aspects/nvim/files/.config/nvim/plugin/mappings/normal.lua#L56-L58)
- `CTRL-^`: go to previous buffer (suggested mapping: `<Leader><Leader>`).
- `gf`: go to file under cursor.
- `CTRL-W f`: go to file under cursor, in split.

## Editor fundamentals

- Motions
  - `h`, `j`, `k`, `l` for movement
  - `gj`, `gk` for virtual movement
  - `w` forward to beginning of word, or `W` (WORD)
  - `b` back to beginning of word, or `B` (WORD)
  - `e` forward to end of word, or `E` (WORD)
  - `ge` back to end of last word, or `gE` (WORD)
- `f` (mnemonic: "find"), `F` (in reverse)
- `t` (mnemonic: "up to", "until"), `T` (in reverse)
- `;` repeat last `f`/`F`/`t`/`T` operation
- `,` repeat last `f`/`F`/`t`/`T` operation, but in opposite direction
- `.`
- `*`, `#` + `n`/`N`
- `/{pattern}` + `?{pattern}`
- Composite commands:
  - `xp`: swap two characters (really, `x`, `p`).
  - `ggn`: go to first match in file (really, `gg` + `n`).
  - `GN`: go to last match in file (really, `G` + `N`).
- Common editor operations
  - `o` open line below for editing in INSERT mode.
  - `O` open line above for editing in INSERT mode.
  - `A` enter INSERT mode at end of line.
  - `I` enter INSERT mode at beginning of line.
- Useful "fundamental" plugins:
  - repeat.vim: https://github.com/tpope/vim-repeat (repeat entire mapping instead of last thing in it).
  - surround.vim: https://github.com/tpope/vim-surround
    - `cs{from}{to}`: change surrounds.
    - `ds{delimiter}`: delete surrounds.
    - `ys{motion}{delimiter}`: add surrounds (mnemonic: "yes, surround").

## Tools

- Marks
  - `a-z` are in-file marks, `A-Z` are global marks.
  - Special marks include:
    - `[`: last yanked text.
    - `<`: last visual selection (`>` is end of last visual selection).
    - `^`: last place we left INSERT mode.
    - `.`: place where last change was made.
  - Set a mark: `:mark {mark}` (or shorter, `:k{mark}`).
  - Go to mark <code>`{mark}</code> (exact position within line).
  - Go to mark `'{mark}` (beginning of line contents).
  - For convenience: https://github.com/kshenoy/vim-signature
    - `m{mark}`: to toggle mark; `m,` to place next available mark.
    - `dm{mark}`: delete a mark.
  - Jumping between marks without naming them:
    - `]'` next (or <code>]`</code>).
    - `['` previous (or <code>[`</code>).
- Registers
  - `:di`/`:registers`
  - `"{register}y{motion}` and `"{register}p` or `"{register}P`
- Macros
  - Recording a macro: `q{register}` (uppercase appends).
  - Replaying a macro: `@{register}` (`@@` repeats last replay command).
  - Editing macros: `"{register}p` → edit → `"{register}yy`
    - `<CTRL-v>` can be handy here for typing literal control characters.
  - Replay plug-in: https://github.com/wincent/replay (default mapping: `<CR>`)
- Command-mode tricks:
  - Global operations
    - `:g/foo/ d` delete lines matching "foo" (`d` is an "Ex" command; can use others, like `:s` etc).
    - `:v/foo/ d` delete lines not matching "foo".
    - `:%sort` sort everything (`:%sort n` sort numerically; for other modifiers, see `:h :sort`).
  - Regex patterns:
    - Magic and "very magic":
      - Loupe: https://github.com/wincent/loupe
    - Perlisms in Vim syntax (these in "very magic" syntax):
      - Non-greedy mappings:
        - `a{-}` (ie. like `a*?`)
        - `a{-1,}` (ie. like `a+?`)
      - Positive look-ahead (zero-width match): `ab@=` (ie. like `a(?=b)`).
      - Negative look-behind (zero-width match): `ab@!` (ie. like `a(?!b)`).
      - Positive look-behind (zero-width match): `a@<=b` (ie. like `a($<=b)`).
      - Negative look-behind (zero-width match): `a@<!` (ie. like `a(?<!b)`).
      - Easy to remember:
        - `\zs` do a zero-width match anywhere, setting start of match to that position; eg:
          - Positive look-behind: `a\zsb`
        - `\ze` do a zero-width match anywhere, setting end of match to that position; eg:
          - Positive look-ahead: `a\zeb`
    - Replacement modifiers:
      - `\u` makes next character uppercase
      - `\U` makes everything uppercase until `\E`/`\e`
      - `\l` makes next character lowercase
      - `\L` makes everything lowercase until `\E`/`\e`

## Miscellaneous tips

- Indenting and dedenting:
  - VISUAL mode: `>>`, `<<`
  - INSERT mode: `CTRL-d` (mnemonic: "dedent"), `CTRL-t` (mnemonic: "tab")
- In INSERT mode, `CTRL-O` to execute one command and return to insert mode.
- `gv` reselect last VISUAL selection
- `ga` show ASCII value at current position
- `g8` show UTF-8 value at current position
- `g CTRL-g` show current cursor position and total counts (columns, lines, words, bytes)
- `gu{motion}` make lowercase
- `gU{motion}` make uppercase
- `g~{motion}` toggle case
- `gq{motion}` format lines
- `CTRL-a` increment number
- `CTRL-x` decrement number
- In INSERT mode, `CTRL-r ={expr}` to insert the value of an expression.

## Customizing Vim

- Leader mappings:
  - `:let mapleader = " "` (Vimscript), or `vim.g.mapleader = ' '` (Lua)
  - [`~/.config/nvim/plugin/mappings/leader.lua`](https://github.com/wincent/wincent/blob/b94dafbe4caefa76305e90a37ad9342264fff5af/aspects/nvim/files/.config/nvim/plugin/mappings/leader.lua)
- Local leader:
  - `:let maplocalleader = "\\"` (Vimscript), or `vim.g.maplocalleader = '\\'` (Lua)
- ftplugins
  - `'gitcommit'`: [`~/.config/nvim/ftplugin/gitcommit.lua`](https://github.com/wincent/wincent/blob/b94dafbe4caefa76305e90a37ad9342264fff5af/aspects/nvim/files/.config/nvim/ftplugin/gitcommit.lua)
  - `'markdown'`: [`~/.config/nvim/ftplugin/markdown.lua`](https://github.com/wincent/wincent/blob/b94dafbe4caefa76305e90a37ad9342264fff5af/aspects/nvim/files/.config/nvim/ftplugin/markdown.lua)
- Lua
  - https://wincent.dev/wiki/Lua_development_in_Neovim
- Useful plug-ins:
  - undotree: https://github.com/mbbill/undotree
  - vim-easydir: https://github.com/duggiefresh/vim-easydir
  - vim-fugitive: https://github.com/tpope/vim-fugitive
  - vim-lion: https://github.com/tommcdo/vim-lion
  - And many others: https://github.com/wincent/wincent/blob/main/.gitmodules
- Pro-tip™️: Map `<leader>q` to `:q`, to avoid accidentally typing `q:`.
- Useful settings
  - `'colorcolumn'`
  - `'cursorline'`
  - `'shortmess'`
  - `'switchbuf'` (see `usetab`, `uselast`)
  - `'virtualedit'` (`block`)

## Debugging and troubleshooting

- `:verbose set ...?`
- `:verbose map <prefix>`
- `'verbose'` and `'verboselog'`
- Startup profiling: `vim --startuptime log.txt`

## Resources

- Screencasts and streams:
  - [@greghurrell (YouTube)](https://wincent.dev/link/screencasts)
  - [@teej_dv (Twitch)](https://www.twitch.tv/teej_dv)
  - [@ThePrimeagen (Twitch)](https://www.twitch.tv/theprimeagen)
  - [vimcasts.org](http://vimcasts.org/)
- Forums:
  - [/r/neovim](https://www.reddit.com/r/neovim)
  - [/r/vim](https://www.reddit.com/r/vim/)
  - [neovim/neovim (Gitter)](https://gitter.im/neovim/neovim)
- Books:
  - ["Practical Vim" by Drew Neil](https://pragprog.com/titles/dnvim2/practical-vim-second-edition/)
  - ["Vim Reference Guide" by Sundeep Agarwal](https://learnbyexample.github.io/vim_reference/)
- Games and challenges:
  - [www.vimgolf.com](https://www.vimgolf.com/)
