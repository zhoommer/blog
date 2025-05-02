---
title: 'Why Neovim Became My Daily Driver'
description: 'Neovim'
pubDate: 'May 05 2025'
heroImage: '/lazyvim.png'
---

Choosing a text editor among developers has become less of a debate and more of a statement of identity.
While some remain loyal to the plugin-rich ecosystem of Visual Studio Code or the comprehensive features of JetBrains IDEs, I chose Neovim. In this article, I’ll explain why I embraced Neovim and how it supports me in my daily workflow.

##### Minimalism and Fast Performance
Neovim offers a minimal structure. Instead of the many visual interface elements found in modern editors, it provides a pure and efficient text editing experience. As a result, Neovim runs much faster and is lightweight in terms of resource usage. You can write code effectively without overloading your computer’s resources.

##### Customizability
Another major advantage of Neovim is its fully customizable nature. You can shape your working environment with custom keybindings, color themes, and plugins to fit your needs. By using preconfigured plugin bundles like LazyVim, you can also save time on setup.

##### Productivity with LazyVim
LazyVim is a great tool that highlights Neovim’s customizability. It makes installing and using Neovim much easier. This is especially beneficial for developers who want to avoid complex configuration processes.

##### Fast Searching with Fzf
Neovim becomes even more powerful with plugins like Fzf (“Fuzzy Finder”), which allows for lightning-fast file and text searches. This can save a lot of time, especially in large projects, and helps you find exactly what you’re looking for in seconds.

##### Efficiency with Keyboard Shortcuts
Neovim’s keyboard shortcuts make the coding process much smoother. 
Here are some examples:

##### 🧭 Navigation
```markdown
| Key                 | Action                                          |
| ------------------- | ----------------------------------------------- |
| `h`, `j`, `k`, `l`  | Move left, down, up, right                      |
| `w` / `W`           | Move forward by word (W = whitespace-separated) |
| `b` / `B`           | Move backward by word                           |
| `0` / `^` / `$`     | Start / first non-whitespace / end of line      |
| `gg` / `G`          | Start / end of file                             |
| `Ctrl-d` / `Ctrl-u` | Scroll half page down / up                      |
| `%`                 | Jump to matching bracket/parenthesis            |
```

##### ✏️  Editing
```markdown
| Key       | Action                                 |
| --------- | -------------------------------------- |
| `i` / `I` | Insert mode / insert at line start     |
| `a` / `A` | Append after cursor / at line end      |
| `o` / `O` | Open new line below / above            |
| `x` / `X` | Delete character under / before cursor |
| `dd`      | Delete (cut) current line              |
| `yy`      | Yank (copy) current line               |
| `p` / `P` | Paste after / before cursor            |
| `u`       | Undo last action                       |
| `Ctrl-r`  | Redo                                   |
```

##### 🔍 Search & Replace
```markdown
| Key             | Action                               |
| --------------- | ------------------------------------ |
| `/word`         | Search forward                       |
| `?word`         | Search backward                      |
| `n` / `N`       | Repeat search forward / backward     |
| `:%s/old/new/g` | Replace all `old` with `new` in file |
| `:noh`          | Clear search highlight               |
```
##### 🎯 Useful Commands
```markdown
| Command               | Action                           |
| --------------------- | -------------------------------- |
| `:e filename`         | Open a file                      |
| `:w` / `:q` / `:wq`   | Save / quit / save & quit        |
| `:vsp filename`       | Vertical split                   |
| `:sp filename`        | Horizontal split                 |
| `Ctrl-w h/j/k/l`      | Move between splits              |
| `:buffers` / `:bnext` | Show buffers / go to next buffer |
```

##### 🔁 Macros
```markdown
| Key  | Action                                  |
| ---- | --------------------------------------- |
| `qa` | Start recording macro into register `a` |
| `@a` | Play macro from register `a`            |
| `@@` | Repeat last macro                       |
```


##### Community and Documentation
Neovim has an active community and rich documentation. If you ever encounter a problem, it’s easy to find support through community forums, GitHub repositories, and guides.

##### A Deeper Connection
Using Neovim helps you feel a deeper connection to your tools. Creating your own key mappings and plugins allows you to take your coding process to the next level of mastery.

##### Conclusion
Neovim goes beyond being a simple text editor—it offers developers full control and freedom in their workflow. If you’re looking to improve your development process and enjoy a more minimalistic experience, you should definitely consider giving Neovim a try.
