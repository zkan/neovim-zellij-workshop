# Neovim and Zellij Together

การใช้ Neovim กับ Zellij จะช่วยทำให้เราเข้าสู่ flow state ได้

![](./img/grok-developer-in-the-flow-state-coding-intensely-in-a-dimly-lit-room-with-a-blurred-background.jpg)

**หมายเหตุ:** รูปถูกสร้างโดยใช้ Grok กับ prompt "developer in the flow state coding intensely in a dimly lit room with a blurred background"

```lua
-- Ruby
local run_ruby_test = function()
  local current_file = vim.fn.expand('%:p')
  local test_string = "silent !zellij run -d Down -n 'testing' -- ruby " .. current_file
  vim.api.nvim_command(test_string)
end
```

```lua
-- Rails
local run_test = function()
  local current_file = vim.fn.expand('%:p')
  local test_string = "silent !zellij run -d Down -n 'testing' -- bin/rails test " .. current_file
  vim.api.nvim_command(test_string)
end
```

```lua
local run_all_tests = function()
  local test_string = "silent !zellij run -d Down -n 'testing' -- bin/rails test"
  vim.api.nvim_command(test_string)
end
```

```lua
vim.api.nvim_create_user_command('RunRubyTest', run_ruby_test, {})
vim.api.nvim_create_user_command('RunTest', run_test, {})
vim.api.nvim_create_user_command('RunAllTests', run_all_tests, {})

vim.keymap.set("n", "<leader>r", ":RunRubyTest<CR>", { desc = "run current file test" })
vim.keymap.set("n", "<leader>t", ":RunTest<CR>", { desc = "run current file test" })
vim.keymap.set("n", "<leader>a", ":RunAllTests<CR>", { desc = "run all tests" })
```