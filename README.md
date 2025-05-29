**1Cactus-gg-Library 🌵🚀**

Lightweight Roblox executor GUI library designed to make your scripts look slick AF. This README will walk you through setup, API, and examples—so you can get back to pwning noobs. 😎

---

## 🚀 Installation

Just load it in your executor script:

```lua
local Menu = loadstring(game:HttpGet("https://raw.githubusercontent.com/khenn791/library/refs/heads/main/cuh.txt", true))()
Menu:SetSize(500, 400)  -- width, height
```

That's it—you're ready to roll.

---

## 🎛️ API Reference

### Creating Tabs

```lua
local mainTab     = Menu:Tab("Main")       -- Your main tab
local settingsTab = Menu:Tab("Settings")   -- Another tab
```

### Adding Sections (Containers)

```lua
-- tab: Container(name, position)
local testSec    = mainTab:Container("Test",    "Left")
local hitPartSec = mainTab:Container("HitPart", "Left")
local inputSec   = mainTab:Container("Inputs",  "Right")
```

### CheckBox

```lua
testSec:CheckBox("Toggle Label", "Enabled", function(state)
    print("Checkbox state:", state)
end)
```

### Button

```lua
testSec:Button("Button ID", "Eat My Toes", function()
    print("Toes eaten 🍽️")
end)
```

### TextBox

```lua
inputSec:TextBox("TextBox ID", "Change here", "input", function(input)
    print("User input:", input)
end)
```

### Slider

```lua
inputSec:Slider(
    "Slider ID",        -- unique ID
    "Step Value",       -- label
    0,                   -- min
    20,                  -- max
    0,                   -- default
    1,                   -- step
    function(val)
        print("Slider val:", val)
    end
)
```

### ComboBox

```lua
local Settings = { SelectedHitPart = "Head" }

hitPartSec:ComboBox(
    "BodyPart ID",      -- ID
    "Body Part",        -- label
    {                    -- options
        "Head","UpperTorso","LowerTorso","HumanoidRootPart",
        -- ...other parts
    },
    function(selection)
        Settings.SelectedHitPart = selection
        print("Selected part:", selection)
    end
)
```

---

## 📝 Example Full Setup

```lua
-- Load & init
local Menu = loadstring(game:HttpGet("https://raw.githubusercontent.com/khenn791/library/refs/heads/main/cuh.txt", true))()
Menu:SetSize(500, 400)

-- Tabs & Sections
local mainTab    = Menu:Tab("Main")
local testSec    = mainTab:Container("Test",    "Left")
local hitPartSec = mainTab:Container("HitPart", "Left")
local inputSec   = mainTab:Container("Inputs",  "Right")

-- State
local Settings = { SelectedHitPart = "Head", StepValue = 0 }

-- Controls

-- Toggle
testSec:CheckBox("Toggle Label", "Enabled", function(state)
    print(state)
end)

-- Button
testSec:Button("toeBtn", "Eat My Toes", function()
    print("🍽️ Toes eaten")
end)

-- TextBox
inputSec:TextBox("txt1", "Type here", "input", function(input)
    print(input)
end)

-- Slider
inputSec:Slider("stepSlider","Step",0,20,Settings.StepValue,1, function(val)
    Settings.StepValue = val
    print("Step set to:", val)
end)

-- ComboBox
hitPartSec:ComboBox("hitPartCB","Body Part",{
    "Head","UpperTorso","LowerTorso","HumanoidRootPart",
    -- etc
}, function(sel)
    Settings.SelectedHitPart = sel
    print("Hit part:", sel)
end)
```

---

## 💡 Tips & Tricks

* **Always use unique IDs** for each control to avoid clashes.
* **Chain methods** like `tab:Container` and `section:Button` for readability.
* **Store state** in a table (e.g. `Settings`) for easy access.

---

© 2025 1Cactus-gg | Made for chill devs who wanna flex in Roblox executors 😜
