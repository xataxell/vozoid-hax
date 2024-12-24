# vozoid hax
ui library thing

# Documentation
> [!NOTE]
> This UI Library might not work on certain executors, the only one that it has been tested and confirmed to work on is awp.gg

> Loading the library
```lua
local library = loadstring(game:HttpGet('https://raw.githubusercontent.com/xataxell/vozoid-hax/refs/heads/main/source.lua'))()
```

> Creating, setting and toggling the visibility a watermark
```lua
local watermark = library:Watermark('vozoid hax | private dev build | v1.0.0 | 240 fps | 15 ms')
```
```lua
watermark:Set('updated watermark')
```
```lua
watermark:Hide()
```
