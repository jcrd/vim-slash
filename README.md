vim-slash
=========

vim-slash provides a set of mappings for enhancing in-buffer search experience
in Vim.

- Automatically clears search highlight when cursor is moved
- Improved star-search (visual-mode, highlighting without moving)

This fork's differences
-----------------------

- Merges [this](https://github.com/junegunn/vim-slash/pull/16) pull request,
fixing a long-standing [issue](https://github.com/junegunn/vim-slash/issues/14)
with visual star search.
- Saves and clears the search register instead of setting `nohlsearch` to turn
off highlighting when the cursor moves. This allows neovim's
[`inccommand`](https://neovim.io/doc/user/options.html#'inccommand') option to
be used along with this plugin.
- Removes cursor blinking functionality, ~as it's reportedly
[broken](https://github.com/junegunn/vim-slash/issues/17) in neovim~ and it does
not benefit vim-slash's feature set.
- Exposes search clearing functionality as `SlashClearSearch()`. This can be
called after a substitute command in which some matches are skipped,
e.g., `:%s/search/replace/gc`, as those matches remain highlighted.

Installation
------------

Using [vim-plug](https://github.com/junegunn/vim-plug):

```vim
Plug 'junegunn/vim-slash'
```

Comparison with vim-oblique
---------------------------

vim-slash is a smaller alternative to [vim-oblique][ob]. vim-oblique depends
on [a reimplementation of Vim command-line interface][pcl] which is incomplete
and has a number of issues that cannot be easily fixed. vim-oblique is also
much slower than the native /-search when working with large files.

Many features of vim-oblique are missing in vim-slash, but [frankly, my dear,
I don't give a damn][damn].

[ob]:   https://github.com/junegunn/vim-oblique
[pcl]:  https://github.com/junegunn/vim-pseudocl
[damn]: https://en.wikipedia.org/wiki/Frankly,_my_dear,_I_don%27t_give_a_damn

Customization
-------------

#### `zz` after search

Places the current match at the center of the window.

```vim
noremap <plug>(slash-after) zz
```
