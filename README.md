# vozoid hax
ui library thing

# Documentation
> [!NOTE]
> This UI Library might not work on certain executors, the only one that it has been tested and confirmed to work on is awp.gg

> Loading the library
```lua
local library = loadstring(game:HttpGet('https://raw.githubusercontent.com/xataxell/vozoid-hax/refs/heads/main/source.lua'))()
```
‭
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
‭
> Creating the main UI
```lua
local main = library:Load{
    Name = 'vozoid hax',
    SizeX = 600,
    SizeY = 650,
    Theme = 'Midnight', -- 2nd theme (built-in themes: Defalt, Midnight)
    Extension = 'json', -- config file extension
    Folder = 'vozoid hax' -- config folder name
}
```
‭
> Tab creation
```lua
local tab1 = main:Tab('Tab 1')
local tab2 = main:Tab('Tab 2')
```

> Sections
```lua
local leftsection = tab1:Section{
    Name = 'left section',
    Side = 'Left'
}
local rightsection = tab2:Section{
    Name = 'right section',
    Side = 'Right'
}
```
