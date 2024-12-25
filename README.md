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
watermark:Toggle(true) -- Makes it visible, change it to false to make it invisible (hide it)
```
‭
> Creating the main UI
```lua
local main = library:Load{
    Name = 'vozoid hax',
    SizeX = 600,
    SizeY = 650,
    Theme = 'Midnight', -- 2nd theme (built-in themes: Defalt, Midnight, Gamesense)
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
> Certain elements such as keybinds, colorpickers, sliders and maybe more can be connected to other elements such as toggles, example below:
```lua
toggle:ColorPicker{params}
toggle:Keybind{params}
toggle:Slider{params}
```
‭
> Toggles & Connected Colorpickers & Connected Keybinds
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
        print('left section toggle colorpicker color is now ' .. (math.round(color.R * 255)) .. ' ' .. math.round(color.G * 255) .. ' ' .. math.round(color.B * 255) .. ' ' .. (math.round(color.A * 100) / 100)) -- color units changed from max 0-1 to max 0-255 and then rounded the alpha (transparency) to the alpha times 100 and then divided so its a smooth number with a max of 2 decimal places
    end
}
```
```lua
local leftsection_toggle_colorpicker_2 = toggle:ColorPicker{
    Default = Color3.fromRGB(0, 255, 0), 
    Flag = 'leftsection_toggle_colorpicker2', 
    Callback = function(color)
        print('left section toggle colorpicker color is now ' .. (math.round(color.R * 255)) .. ' ' .. math.round(color.G * 255) .. ' ' .. math.round(color.B * 255) .. ' ' .. (math.round(color.A * 100) / 100))-- color units changed from max 0-1 to max 0-255 and then rounded the alpha (transparency) to the alpha times 100 and then divided so its a smooth number with a max of 2 decimal places
    end
}
```
```lua
local leftsection_toggle_colorpicker_3 = toggle:ColorPicker{
    Default = Color3.fromRGB(0, 0, 255), 
    Flag = 'leftsection_toggle_colorpicker3', 
    Callback = function(color)
        print('left section toggle colorpicker color is now ' .. (math.round(color.R * 255)) .. ' ' .. math.round(color.G * 255) .. ' ' .. math.round(color.B * 255) .. ' ' .. (math.round(color.A * 100) / 100)) -- color units changed from max 0-1 to max 0-255 and then rounded the alpha (transparency) to the alpha times 100 and then divided so its a smooth number with a max of 2 decimal places
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
    Flag = 'lefsection_slider',
    Callback = function(value)
        print("Toggle 3 Slider 1 is now " .. value)
    end
```
‭
> Dropdowns
```lua
local singledropdown = leftsection:Dropdown{
    Name = 'Single Dropdown',
    Default = 'Option 1', -- string
    Content = {'Option 1', 'Option 2', 'Option 3'},
    Flag = 'singledropdown',
    Callback = function(option)
        print('single dropdown selection: ' .. tostring(option))
    end
}
```
```lua
local multidropdown = leftsection:Dropdown{
    Name = 'Multi Dropdown',
    Default = {'Option 1', 'Option 2'}, -- table with strings
    Max = 3, -- this makes it a multi dropdown
    Content = {'Option 1', 'Option 2', 'Option 3'},
    Flag = 'multidropdown',
    Callback = function(option)
        print('multi dropdown selection: ' .. table.concat(option, ', '))
    end
}
```
```lua
local scrollabledropdown = leftsection:Dropdown{
    Name = 'Scrollable Dropdown',
    Default = 'Option 1', -- string
    Scrollable = true, -- Makes it scrollable
    ScrollingMax = 3, -- caps the amount of options it contains before scrolling
    Content = {'Option 1', 'Option 2', 'Option 3', 'Option 4', 'Option 5', 'Option 6', 'Option 7', 'Option 8', 'Option 9', 'Option 10'},
    Flag = 'scrollabledropdown',
    Callback = function(option)
        print('scrollable dropdown selection: ' .. tostring(option))
    end
}
```
```lua
singledropdown:Set('Option 2') -- sets the selected option in the single dropdown to Option 2
singledropdown:Set() -- entering no arguments or the wrong arguments will cause the dropdown to be unset (which means nothing will be selected)
```
```lua
singledropdown:Refresh{'New option 1', 'New option 2', 'New option 3'} -- sets the new content for the dropdown
```
```lua
singledropdown:Add('Option 4') -- Adds to the content
singledropdown:Remove('Option 4') -- Removes from the content
```
```lua
multidropdown:Set('Option 2') -- sets the selected option in the multi dropdown to Option 2
multidropdown:Set{'Option 1', 'Option 2'} -- sets the selected options in the multi dropdown to Option 1 and Option 2
multidropdown:Set() -- entering no arguments or the wrong arguments will cause the dropdown to be unset (which means nothing will be selected)
multidropdown:Set{} -- entering no arguments or the wrong arguments will cause the dropdown to be unset (which means nothing will be selected)
```
