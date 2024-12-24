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
‭
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
‭
> Labels
```lua
local label = leftsection:Label('label for left section')
```
‭‭
> Buttons
```lua
leftsection:Button{
    Name = 'button for left section',
    Callback  = function()
        print('the button in the left section has been clicked')
    end
}
```
‭
> Seperators
```lua
local seperator = leftsection:Separator('seperator')
```
```lua
seperator:Set('seperator for left section')
```
‭
> [!TIP]
> Certain elements such as keybinds, colorpickers, sliders and maybe more can be connected to other elements such as toggles
> Example:
```lua
toggle:ColorPicker{params}
toggle:Keybind{params}
toggle:Slider{params}
```
‭
> Toggles
```lua
local toggle = leftsection:Toggle{
    Name = 'toggle for left section',
    Flag = 'leftsection_toggle', -- flag can be literally anything, it just has to be a string
    Default = false,
    Callback  = function(boolean)
        print('toggle for left section has a value of ' .. boolean)
    end
}
local toggle2 = leftsection:Toggle{
    Name = 'toggle for left section with keybind',
    Flag = 'leftsection_toggle_withkeybind', -- flag can be literally anything, it just has to be a string
    Default = false,
    Callback  = function(boolean)
        print('toggle for left section with keybind has a value of ' .. boolean)
    end
}
```
```lua
local leftsection_toggle_colorpicker_1 = toggle:ColorPicker{
    Default = Color3.fromRGB(255, 0, 0), 
    Flag = 'leftsection_toggle_colorpicker1', 
    Callback = function(color)
        print('left section toggle colorpicker color is now ' .. (math.round(color.R * 255)) .. math.round(color.G * 255) .. math.round(color.B * 255) .. (math.round(color.A * 100) / 100)) -- color units changed from max 0-1 to max 0-255 and then rounded the alpha (transparency) to the alpha times 100 and then divided so its a smooth number with a max of 2 decimal places
    end
}
```
```lua
local leftsection_toggle_colorpicker_2 = toggle:ColorPicker{
    Default = Color3.fromRGB(0, 255, 0), 
    Flag = 'leftsection_toggle_colorpicker2', 
    Callback = function(color)
        print('left section toggle colorpicker color is now ' .. (math.round(color.R * 255)) .. math.round(color.G * 255) .. math.round(color.B * 255) .. (math.round(color.A * 100) / 100)) -- color units changed from max 0-1 to max 0-255 and then rounded the alpha (transparency) to the alpha times 100 and then divided so its a smooth number with a max of 2 decimal places
    end
}
```
```lua
local leftsection_toggle_colorpicker_3 = toggle:ColorPicker{
    Default = Color3.fromRGB(0, 0, 255), 
    Flag = 'leftsection_toggle_colorpicker3', 
    Callback = function(color)
        print('left section toggle colorpicker color is now ' .. (math.round(color.R * 255)) .. math.round(color.G * 255) .. math.round(color.B * 255) .. (math.round(color.A * 100) / 100)) -- color units changed from max 0-1 to max 0-255 and then rounded the alpha (transparency) to the alpha times 100 and then divided so its a smooth number with a max of 2 decimal places
    end
}
```
```lua
toggle2:Keybind{
    Default = Enum.KeyCode.T, -- https://create.roblox.com/docs/reference/engine/enums/KeyCode | https://create.roblox.com/docs/reference/engine/enums/UserInputType
    Blacklist = {Enum.UserInputType.MouseButton1}, -- https://create.roblox.com/docs/reference/engine/enums/KeyCode | https://create.roblox.com/docs/reference/engine/enums/UserInputType
    Flag = 'leftsection_toggle_withkeybind_keybind',
    Mode = 'Toggle', -- mode to nil if u dont want it to toggle the toggle
    Callback = function(key, fromsetting)
        if fromsetting then
            print("Toggle 2 Keybind 1 is now " .. tostring(key))
        else
            print("Toggle 2 Keybind 1 was pressed")
        end
    end
}
```
‭
> Sliders
```lua
leftsection:Slider{
    Text = '[value]/5', -- [value] is always converted to actual slider value (example: 1/5, 6/10, etc.)
    Default = 1,
    Min = 0,
    Max = 5,
    Float = 0.5, -- increment
    Flag = '',
    Callback = function(value)
        print("Toggle 3 Slider 1 is now " .. value)
    end
```
