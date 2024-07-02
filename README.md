# filename-ls

This is plugin simulate a language server to provide codelens for filenames in the current document.

It uses `treesitter` to parse the document looking for filenames and then provides codelens for them, which can be used to open the file in the editor.

[![asciicast](https://asciinema.org/a/666439.svg)](https://asciinema.org/a/666439)

## Requirements

- Neovim 0.10 or later

## Languages supported:

Language | Queries
--- | ---
Go | `//go:embed <filename>`
Yaml | `kustomization` resources block

Contributions for more languages and locations are very much welcome. Take a look at `after/queries` to see how the queries are implemented.

The plugin looks for `@filename` capture groups in the queries to get the file names.

There's initial support for setting folder paths for the files, but it's very much a wip.

## Installation

Using lazy:

```lua
{
    'GustavoKatel/filename-ls',
    opts = {},
}
```

## Default configuration

```lua
{
    -- Icon to show in the codelens. Default to use a nerdfont file icon
    -- It can be a function that receives the filename and folder and returns a string (fun(filename: string, folder: string): string)
	hint = " ", 

    -- list of filetypes to attach the lsp, they also need to have queries implemented for them
	filetypes = {
		"yaml",
		"go",
	},
}
```
