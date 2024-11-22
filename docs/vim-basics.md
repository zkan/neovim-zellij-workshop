# Vim Basics

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">I&#39;ve been using Vim for about 2 years now, mostly because I can&#39;t figure out how to exit it.</p>&mdash; I Am Devloper (@iamdevloper) <a href="https://twitter.com/iamdevloper/status/435555976687923200?ref_src=twsrc%5Etfw">February 17, 2014</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Vim มาจากคำว่า Vi IMproved เป็น open-source cross-platform text editor ตัวหนึ่ง
พัฒนาโดย [Bram Moolenaar](https://en.wikipedia.org/wiki/Bram_Moolenaar)
และถุกปล่อยออกมาใช้งานตั้งแต่ปี 1991

## Understanding Vim Modes

Vim มีโหมดที่ใช้หลัก ๆ ตามนี้

1. **Normal:** เป็นโหมด default ที่เราสามารถที่จะเลื่อนหรือสำรวจข้อความ สั่งคำสั่ง
   และย้ายไปโหมดอื่น เข้าโหมด normal โดยการกด `Esc` จากโหมดไหนก็ได้

1. **Insert:** เป็นโหมดที่ใช้สำรับเพิ่มหรือแก้ไขข้อความ เข้าโหมด insert โดยการกด

    * `i` (insert before cursor)
    * `a` (append after cursor)
    * `o` (open a new line below current line and enter insert mode)
    * `O` (open a new line above current line and enter insert mode)

1. **Visual:** สำหรับ selecting ข้อความ เข้าโหมด visual โดยการกด

    * `v` (character-wise selection)
    * `V` (line-wise selection)
    * `Ctrl+v` (block-wise selection)

1. **Command-line:** สำหรับการสั่งคำสั่ง หรือใช้ค้นหาคำ เข้าโหมด command-line โดยการกด
   `:` (colon)

ดูโหมดอื่น ๆ เพิ่มเติมได้ที่ [Vim documentation:
intro](https://vimdoc.sourceforge.net/htmldoc/intro.html#vim-modes-intro)

## Opening a File

เปิดไฟล์เราใช้คำสั่ง

```bash
vim <file_name>
```

ตอนที่เราอยู่ใน Vim แล้ว ที่โหมด normal

* `:w` สำหรับการเซฟไฟล์ หรือ `:w <new_file_name>` เพื่อเซฟไฟล์ใหม่ตามชื่อที่กำหนด

### Let's Implement a FizzBuzz Program

เราจะมาหัดใช้ Vim โดยการใช้ภาษา Ruby ทำโจทย์ [FizzBuzz](https://en.wikipedia.org/wiki/Fizz_buzz) กัน

File: `test/fizzbuzz_test.rb`

```ruby
require "minitest/autorun"
require_relative "../fizzbuzz"

class FizzBuzzTest < Minitest::Test
  def test_it_should_get_fizz_when_input_is_3
    result = fizzbuzz(3)
    assert_equal "Fizz", result
  end
end
```

File: `fizzbuzz.rb`

```ruby
def fizzbuzz(number)
  "Fizz"
end
```

รันคำสั่ง

```sh
ruby test/fizzbuzz_test.rb
```

เดี๋ยวเราจะมาค่อย ๆ ทำต่อให้จบกัน 😎

## Saving and Quitting

* `:q` เพื่อออกจาก Vim หรือใช้ `:q!` เพื่ออกจาก Vim แบบ force (ไม่เซฟไฟล์)
* `:wq` หรือ `ZZ` เพื่อเซฟ และออกจาก Vim

## Basic Navigation

* `h`, `j`, `k`, `l` for left, down, up, right movement
* `w` to move forward one word, `b` to move backward one word
* `$` to go to the end of the line, `0` to go to the beginning
* `gg` to go to the top of the file, `G` to go to the bottom

## Editing Text

* `x` to delete one character
* `dw` to delete a word, `dd` to delete a line
* `u` to undo the last change, `Ctrl+r` to redo

## Inserting Text

* `i`, `a`, `o` as mentioned for entering Insert Mode
* `I` to insert at the beginning of the line, `A` to append at the end

## Search and Replace

* `/pattern` to search forward for 'pattern'
* `?pattern` to search backward
* `:s/old/new/g` to substitute 'old' with 'new' on the current line. Add `%` after s to apply to the whole file.

## Basic Commands

* `:e filename` to edit another file
* `:sp filename` หรือ `:new filename` to split the window horizontally and edit another file
* `:vsp filename` for vertical split

## Useful Shortcuts

* `yy` to yank (copy) a line, `p` or `P` to paste after or before the cursor respectively.
* `d$` to delete to the end of the line, `d^` to delete to the start.

## Plugins

สามารถไปส่องได้ที่ [Vim Awesome](https://vimawesome.com/) ส่วน plugin manager แนะนำ
[vim-plug](https://junegunn.github.io/vim-plug/) เพราะว่ารู้สึกว่าใช้ง่ายที่สุด
แล้วเค้าก็เคลมว่าเค้าเป็น minimalist design 😂


## Customization

ไฟล์ `~/.vimrc`

```vim
syntax on           " syntax highlighting
set nocompatible    " use vim defaults
set ls=2            " always show status line
set tabstop=4       " numbers of spaces of tab character
set shiftwidth=4    " numbers of spaces to (auto)indent
set expandtab       " insert space characters whenever the tab key is pressed
set autoindent      " always set autoindenting on
set hlsearch        " highlight searches
set incsearch       " do incremental searching
" set number          " show current line number
set relativenumber  " show line numbers
set ignorecase      " ignore case when searching
set title           " set title in console title bar
set ruler           " show the line and column number of the cursor position.
set colorcolumn=100 " show the vertical line at column number 100
set autoread        " Reload unchanged files automatically.

" disable arrow keys
map <Up>    <Nop>
map <Down>  <Nop>
map <Left>  <Nop>
map <Right> <Nop>
```
