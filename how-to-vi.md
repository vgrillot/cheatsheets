
***********
 HOW TO VI
***********

VI cheat sheet: http://www.catswhocode.com/blog/vim-cheat-sheet-for-2016

Character conversion:
=====================

CR/LF Linux conversion:
-----------------------
:set ff=unix


TABSTOP:
--------

http://stackoverflow.com/questions/234564/tab-key-4-spaces-and-auto-indent-after-curly-braces-in-vim

filetype plugin indent on
" show existing tab with 4 spaces width
set tabstop=4
" when indenting with '>', use 4 spaces width
set shiftwidth=4
" On pressing tab, insert 4 spaces
set expandtab

:set list   => display spaces + tabs
:set tabstop=4
:retab      => replace tab by spaces

to cancel an option, add a trailing "!":
:set expandtab!




MACROS:
=======

How to run a macro saved to file ?
vi -s macro_file_name file_name

Play a macro on all files:
for f in QML3Y-OUTA.*; do vi -s macro_fix_map.vim $f; done

http://vim.wikia.com/wiki/Macros
Recording a macro (key sequences):
q<letter><commands>q

Replay a macro:
<number>@<letter>

or

qd  start recording to register d
... your complex series of commands
q   stop recording
@d  execute your macro
@@  execute your macro again



Search:
=======


Global search and replace:
:%s/<oldstr>/<newstr>/g
% for all lines
g for all words in line


Color diff:
diff /path/to/a /path/to/b | vim -R -

or use the VI diff:
vim -d /path/to/a /path/to/b

or pipe any output to VI:
svn diff ... | vi -R -
or diff ... | vi -R -


NAVIGATION:
===========

multi-column editor:
--------------------

CTRL+W, v : split vertical
CTRL+W, s : split horizontal
CTRL+W, c : close a panel
CTRL+W, arrow : move to a panel
CTRL+W, n : new panel

open multiples file in column:
vi file_a file_b -O


line markup:
------------
m, <letter> : set a mark
', <letter> : go to mark

