# Neovim and its Plugin Manager (Lazy)

> Vim-fork focused on extensibility and usability

ดูวิธีติดตั้งได้ที่
[neovim/INSTALL.md](https://github.com/neovim/neovim/blob/master/INSTALL.md){:
target="_blank"}

คำสั่งต่าง ๆ จะเหมือน Vim หมด แล้วก็เวลาเปิดไฟล์จะใช้คำสั่ง `nvim` แทน ตามนี้

```bash
nvim <file_name>
```

!!! tip "ใช้ Alias เรียก `vim` เพื่อเปิด Neovim"

    เราสามารถตั้ง alias เพื่อเปิด Neovim เวลาที่เราสั่ง `vim` โดยการใส่บรรทัดด้านล่างนี้ไว้ใน
    `~/.zshrc` หรือไฟล์ `rc` อื่น ๆ

    ```
    alias vim="nvim"
    ```

Plugin ใน Neovim มีหลายตัวให้เลือกใช้ สำหรับเวิร์คชอปนี้เราจะใช้
[lazy.nvim](https://github.com/folke/lazy.nvim){: target="_blank"} กัน

## วิธีติดตั้ง Lazy

เราจะทำตาม [Installation | lazy.nvim](https://lazy.folke.io/installation) เลย
แบบ Single File Setup (เดี๋ยวเราค่อยปรับเป็นแบบ Structured Setup ในหัวข้อถัด ๆ ไป)

!!! note

    สังเกตว่า configuration ของ Neovim จะเขียนด้วยภาษา Lua

โดยที่ไฟล์ `init.lua` คือไฟล์แรกที่ Neovim จะเข้ามาอ่านทุกครั้งที่เราเปิด Neovim

## ติดตั้ง Plugin ผ่าน Lazy

Plugin แรกที่เราจะลองติดตั้งคือ [Catppuccin for
(Neo)vim](https://github.com/catppuccin/nvim){: target="_blank"} ซึ่งเป็น theme
ของ Neovim เติมความสวยงามน่าใช้ให้กับ Neovim ของเรา

ที่ไฟล์ `~/.config/nvim/init.lua` เราจะเติมโค้ดด้านล่างนี้

```lua
{ "catppuccin/nvim", name = "catppuccin", priority = 1000 }
```

เข้าไปที่ส่วน `spec` ใน `require("lazy").setup` พร้อมกับปรับ `colorscheme` จากเดิมที่เป็น
`"habamax"` ให้เป็น `"catppuccin"` ด้วย สุดท้ายเราจะได้โค้ดตามนี้

```lua
-- Setup lazy.nvim
require("lazy").setup({
  spec = {
    { "catppuccin/nvim", name = "catppuccin", priority = 1000 }
  },
  -- Configure any other settings here. See the documentation for more details.
  -- colorscheme that will be used when installing plugins.
  install = { colorscheme = { "catppuccin" } },
  -- automatically check for plugin updates
  checker = { enabled = true },
})
```

หลังจากนั้นพอเราเปิด Neovim ขึ้นมา plugin ก็จะถูกติดตั้งโดยอัตโมมัติ

แล้วเวลาที่เราอยากเพิ่ม plugin เข้ามา เราก็แค่ไปเพิ่มตรงส่วน `spec` ใน
`require("lazy").setup` เราก็สามารถใช้ plugin ใหม่นั้น ๆ ได้แล้ว

## การจัดโครงสร้างโฟลเดอร์ Neovim Configuration

เราจะมาจัดโครงสร้างโฟลเดอร์ของ Neovim configuration และ plugins กัน
หน้าตาโครงสร้างที่เราจะมาวางกันจะมีหน้าตาแบบนี้

```
~/.config/nvim
├── init.lua
└── lua
    ├── config
    │   ├── globals.lua
    │   ├── keymaps.lua
    │   ├── lazy.lua
    │   └── options.lua
    └── plugins
        ├── catppuccin.lua
        ├── comment.lua
        ├── indent-blankline.lua
        ├── neo-tree.lua
        ├── telescope.lua
        ├── treesitter.lua
        └── which-key.lua
```

Plugins ที่แนะนำให้ใช้ก็จะมีตามที่ใส่ไว้ในโฟลเดอร์ `plugins` ด้านบนเลย
