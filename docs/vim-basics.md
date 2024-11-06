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
