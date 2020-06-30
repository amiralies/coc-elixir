# coc-elixir

Elixir language server extension based on [elixir-ls](https://github.com/elixir-lsp/elixir-ls) for [`coc.nvim`](https://github.com/neoclide/coc.nvim).

## Install

### CocInstall

1. Make sure you've got `elixir` and `mix` available in `$PATH`.

2. Inside (neo)vim run this command:

```
:CocInstall coc-elixir
```

### vim-plug

1. Make sure you've got `elixir`, `mix` and `yarn` available in `$PATH`.

2. Inside your `plug#begin/end` block in your `.vimrc` (vim) or `init.vim` (neovim) file, after `coc.nvim` add:

```
Plug 'amiralies/coc-elixir', {'do': 'yarn install && yarn prepack'}
```

## Features
- Go to definition support
- Code completion
- Inline diagnostic (Build errors and warning)
- Documentation on hover
- Smart closing of code blocks
- Code formatter

## Troubleshooting

### Server fails to start

Upon upgrading `coc-elixir` it is possible that the binary files were compiled
using an OTP or Elixir version that differ from the ones you have installed.
When this happens, the language server will fail to start.

You can build [ElixirLS](https://github.com/elixir-lsp/elixir-ls) yourself to
solve this:

Start by building a binary of ElixirLS from its source:

```
git clone https://github.com/elixir-lsp/elixir-ls.git ~/.elixir-ls
cd ~/.elixir-ls
mix deps.get && mix compile && mix elixir_ls.release -o release
```

Afterwards, create or update your coc-settings file and add this line:

```json
{
  "elixir.pathToElixirLS": "~/.elixir-ls/release/language_server.sh"
}
```

To open your coc-settings file directly from Vim or Nvim, you can use this command:

```
:CocConfig
```

Doing these steps should make this plugin work with [CoC](https://github.com/neoclide/coc.nvim).

## License

MIT

