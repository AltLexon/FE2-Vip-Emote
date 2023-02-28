# FE2-Vip-Emote

## Script:

```lua
local Players = game:GetService('Players')

Players.LocalPlayer.CharacterAdded:Connect(function(Char)
  local script = getsenv(Char.Animate)
  script.changeEmote(1584520816)
end)
```

## How i made?

You have 2 options

1.  debug.setupvalue
2.  getgc()

First we need get the animation id ( you need the emote )

### Setupvalue option

```lua
local Players = game:GetService('Players')
local Character = Players.LocalPlayer.Character
local script = getsenv(Character.Animate)

local id = getupvalues(script.changeEmote)[1].customemote[1].id -- customemote id in animations table

print(id) -- Prints the id
```

### getgc() option

```lua
local function getId()
    for i, v in next, getgc(true) do
        if type(v) == 'table' and rawget(v, 'idle') then -- search a table that contains 'idle'
            return v.customemote[1].id:split('=')[2] -- return the number id
        end
    end
end

print(getId()) -- Prints the id
```
Now we need change the current emote id for the vip one
```lua
local Players = game:GetService('Players')

local script = getsenv(Char.Animate)
script.changeEmote(1584520816--[[Emote Id]])
```
