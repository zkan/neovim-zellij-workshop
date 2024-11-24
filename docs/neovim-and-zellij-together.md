# Neovim and Zellij Together

ในหัวข้อนี้จะอ้างอิงจากโครงสร้างของ Neovim configuration
ที่ทำไว้ในหัวข้อ[การจัดโครงสร้างโฟลเดอร์ Neovim
Configuration](./neovim-lazy.md#neovim-configuration)

## การสั่งรัน Ruby Tests ผ่าน Neovim ใน Zellij

ที่ไฟล์ `~/.config/nvim/lua/config/keymaps.lua` ให้เพิ่ม

```lua
-- Ruby
local run_ruby_test = function()
  local current_file = vim.fn.expand('%:p')
  local test_string = "silent !zellij run -d Down -n 'testing' -- ruby " .. current_file
  vim.api.nvim_command(test_string)
end

vim.api.nvim_create_user_command('RunRubyTest', run_ruby_test, {})

vim.keymap.set("n", "<leader>r", ":RunRubyTest<CR>", { desc = "run current file test" })
```

โค้ดด้านบนจะเป็นการเซต key map ของ Neovim ที่ normal mode เวลาที่กด `<leader>r` ก็จะไปรันฟังก์ชั่น `run_ruby_test`

## การนำไปใช้กับ Rails

```lua
-- Rails
local run_test = function()
  local current_file = vim.fn.expand('%:p')
  local test_string = "silent !zellij run -d Down -n 'testing' -- bin/rails test " .. current_file
  vim.api.nvim_command(test_string)
end

vim.api.nvim_create_user_command('RunTest', run_test, {})

vim.keymap.set("n", "<leader>t", ":RunTest<CR>", { desc = "run current file test" })
```

โค้ดด้านบนจะเป็นการเซต key map ของ Neovim ที่ normal mode เวลาที่กด `<leader>t` ก็จะไปรันฟังก์ชั่น `run_test`

```lua
local run_all_tests = function()
  local test_string = "silent !zellij run -d Down -n 'testing' -- bin/rails test"
  vim.api.nvim_command(test_string)
end

vim.api.nvim_create_user_command('RunAllTests', run_all_tests, {})

vim.keymap.set("n", "<leader>a", ":RunAllTests<CR>", { desc = "run all tests" })
```

โค้ดด้านบนจะเป็นการเซต key map ของ Neovim ที่ normal mode เวลาที่กด `<leader>a` ก็จะไปรันฟังก์ชั่น `run_all_tests`
