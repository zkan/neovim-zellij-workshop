# Vim Basics

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">I&#39;ve been using Vim for about 2 years now, mostly because I can&#39;t figure out how to exit it.</p>&mdash; I Am Devloper (@iamdevloper) <a href="https://twitter.com/iamdevloper/status/435555976687923200?ref_src=twsrc%5Etfw">February 17, 2014</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Vim มาจากคำว่า Vi IMproved เป็น open-source cross-platform text editor ตัวหนึ่ง
พัฒนาโดย [Bram Moolenaar](https://en.wikipedia.org/wiki/Bram_Moolenaar)
และถุกปล่อยออกมาใช้งานตั้งแต่ปี 1991

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

ไฟล์ `~/.vimrc`

```vim
syntax on " syntax highlighting

set nocompatible    " use vim defaults
set ls=2            " always show status line
set tabstop=4       " numbers of spaces of tab character
set shiftwidth=4    " numbers of spaces to (auto)indent
set expandtab       " insert space characters whenever the tab key is pressed
set autoindent      " always set autoindenting on
set hlsearch        " highlight searches
set incsearch       " do incremental searching
set relativenumber  " show line numbers
set number          " show current line number
set ignorecase      " ignore case when searching
set title           " set title in console title bar
set ruler           " show the line and column number of the cursor position.
set colorcolumn=100
set autoread        " Reload unchanged files automatically.

" Map arrow keys to <Nop> to disable its functionality
map <Up>    <Nop>
map <Down>  <Nop>
map <Left>  <Nop>
map <Right> <Nop>
```