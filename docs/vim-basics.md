# Vim Basics

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">I&#39;ve been using Vim for about 2 years now, mostly because I can&#39;t figure out how to exit it.</p>&mdash; I Am Devloper (@iamdevloper) <a href="https://twitter.com/iamdevloper/status/435555976687923200?ref_src=twsrc%5Etfw">February 17, 2014</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Vim มาจากคำว่า Vi IMproved เป็น open-source cross-platform text editor ตัวหนึ่ง
พัฒนาโดย [Bram Moolenaar](https://en.wikipedia.org/wiki/Bram_Moolenaar){: target="_blank"}
และถุกปล่อยออกมาใช้งานตั้งแต่ปี 1991

### Learning Vim with FizzBuzz

เราจะมาหัดใช้ Vim โดยการใช้ภาษา Ruby ทำโจทย์
[FizzBuzz](https://en.wikipedia.org/wiki/Fizz_buzz){: target="_blank"} กัน
ก่อนอื่นให้สร้างโฟลเดอร์เปล่า ๆ ขึ้นมา

```bash
mkdir neovim-zellij-workshop
```

แล้วเดี๋ยวเราจะค่อย ๆ เพิ่มไฟล์ด้านล่างนี้กัน

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

ถ้ารันเทสได้ ไม่ติดปัญหาอะไร เราก็สามารถทำเวิร์คชอปกันต่อได้ล่ะ ซึ่งเดี๋ยวเราจะมาค่อย ๆ เรียนรู้ Vim
และทำโปรแกรม FizzBuzz ต่อให้จบกัน 😎

## Understanding Vim Modes

Vim มีโหมดที่ใช้หลัก ๆ ตามนี้

1. **Normal:** เป็นโหมด default ที่เราสามารถที่จะเลื่อนหรือสำรวจข้อความ สั่งคำสั่ง
   และย้ายไปโหมดอื่น เข้าโหมด normal โดยการกด `Esc` จากโหมดไหนก็ได้

1. **Insert:** เป็นโหมดที่ใช้สำรับเพิ่มหรือแก้ไขข้อความ เข้าโหมด insert โดยการกด

    * `i` (insert before cursor) ส่วน `I` ใช้ insert ที่ต้นบรรทัด
    * `a` (append after cursor) ส่วน `A` ใช้ append ที่ท้ายบรรทัด
    * `o` (open a new line below current line and enter insert mode)
    * `O` (open a new line above current line and enter insert mode)

1. **Visual:** สำหรับ selecting ข้อความ เข้าโหมด visual โดยการกด

    * `v` (character-wise selection)
    * `V` (line-wise selection)
    * `Ctrl+v` (block-wise selection)

1. **Command-line:** สำหรับการสั่งคำสั่ง หรือใช้ค้นหาคำ เข้าโหมด command-line โดยการกด
   `:` (colon)

ดูโหมดอื่น ๆ เพิ่มเติมได้ที่ [Vim documentation:
intro](https://vimdoc.sourceforge.net/htmldoc/intro.html#vim-modes-intro){: target="_blank"}

## Opening a File

เปิดไฟล์เราใช้คำสั่ง

```bash
vim <file_name>
```

ตอนที่เราอยู่ใน Vim แล้ว ที่โหมด normal

* `:w` สำหรับการเซฟไฟล์ หรือ `:w <new_file_name>` เพื่อเซฟไฟล์ใหม่ตามชื่อที่กำหนด

## Saving and Quitting

* `:q` เพื่อออกจาก Vim หรือใช้ `:q!` เพื่ออกจาก Vim แบบ force (ไม่เซฟไฟล์)
* `:wq` หรือ `ZZ` เพื่อเซฟ และออกจาก Vim

## Navigation

* `h`, `j`, `k`, `l` สำหรับไปทาง ซ้าย, ลง, ขึ้น, ขวา ตามลำดับ ([ทำไม `hjkl`](https://dave.cheney.net/2017/08/21/the-here-is-key){: target="_blank"}?)
* `w` ใช้เลื่อนไปข้างหน้า 1 คำ ส่วน `b` ใช้เลื่อนถอยหลัง 1 คำ
* `$` ไปที่ท้ายสุดของบรรทัด ส่วน `0` ไปที่ต้นบรรทัด
* `gg` ไปที่ด้านบนสุดของไฟล์ ส่วน `G` ไปที่ล่างสุด

เพิ่มเติม ถ้าเราพิมพ์ตัวเลขก่อน แล้วค่อย navigate ก็จะเป็นการกระโดดไปเป็นจำนวนตามตัวเลข เช่น
`10k` จะเป็นการ nagivate ไปทางขวา 10 ตัวอักษร เป็นต้น

* `Ctrl+e` เป็นการเลื่อนหน้าจอลง 1 แถว ส่วน `Ctrl+y` เป็นการเลื่อนหน้าจอขึ้น 1 แถว
* `Ctrl+d` เป็น 1/2 page down ส่วน `Ctrl+u` จะเป็น 1/2 page up
* `Ctrl+f` เป็น 1 page down ส่วน `Ctrl+b` จะเป็น 1 page up
* เวลาที่อยากจะกระโดดจากสิ่งที่อยู่คู่กัน เช่น เปิด `{` กับ ปิด `}` ให้เลื่อน cursor ไปบนนั้นแล้วกด `%` ซึ่งสามารถกระโดดย้อนไปย้อนมาได้ (ใช้กับ tag HTML ได้ด้วย)

## Editing Text

* `x` ใช้ลบ 1 อักษร
* `dw` ใช้ลบ 1 คำ ส่วน `dd` ใช้ลบทั้งแถว
* `u` ใช้ undo การเปลี่ยนแปลงล่าสุด ส่วน `Ctrl+r` ใช้ redo
* คลุมแถบดำโดยใช้ `V` เสร็จแล้วกด `U` จะเป็นการเปลี่ยนเป็น upper case ทั้งหมด
* คลุมแถบดำโดยใช้ `V` เสร็จแล้วกด `u` จะเป็นการเปลี่ยนเป็น lower case ทั้งหมด
* ครอบ + `>` จะเป็นการ indent ไปทางขวา ถ้า `<` ก็จะ indent ไปทางซ้าย

## Search and Replace

* `/pattern` ใช้ search หาคำว่า "pattern" แบบ forward
* `?pattern` ใช้ search แบบ backward
* `:s/old/new/g` ใช้ replace คำว่า "old" ด้วยคำว่า "new" ที่บรรทัดที่อยู่ ถ้าเราติม `%` หลัง `s` จะเป็นการ replace ทั้งไฟล์

## Basic Commands

* `:e file_name` ใช้ edit ไฟล์ "file_name"
* `:sp file_name` หรือ `:new file_name` ใช้ split แบบ horizontally เพื่อมา edit
* `:vsp file_name` ใช้ split แบบ vertically

## Useful Shortcuts

* `yy` ใช้สำหรับ yank หรือ copy ทั้งแถ
* `p` or `P` ใช้ใน paste หลัง หรือ ก่อนหน้า cursor ตามลำดับ
* `d$` ใช้ลบตั้งแต่ cursor ไปจนสิ้นสุดบรรทัด ส่วน `d^` ใช้ลบตั้งแต่ cursor ไปจนจุดเริ่มของบรรทัด

## Plugins

สามารถไปส่องได้ที่ [Vim Awesome](https://vimawesome.com/){: target="_blank"} ส่วน
plugin manager แนะนำ [vim-plug](https://junegunn.github.io/vim-plug/){: target="_blank"}
เพราะว่ารู้สึกว่าใช้ง่ายที่สุด แล้วเค้าก็เคลมว่าเค้าเป็น minimalist design 😂


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

## References

* [Vim Cheat Sheet](https://vim.rtorr.com/){: target="_blank"}
