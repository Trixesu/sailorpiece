-- Load Rayfield UI
local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
   Name = "Kertas - Sailor Piece",
   LoadingTitle = "Loading...",
   LoadingSubtitle = "Kertas",
   ConfigurationSaving = {
      Enabled = false
   }
})

-- Services
local vim = game:GetService("VirtualInputManager")
local vu = game:GetService("VirtualUser")
local player = game:GetService("Players").LocalPlayer

-- Anti AFK
player.Idled:Connect(function()
    vu:Button2Down(Vector2.new(0,0), workspace.CurrentCamera.CFrame)
    wait(1)
    vu:Button2Up(Vector2.new(0,0), workspace.CurrentCamera.CFrame)
end)

-- Variables
local selectedKeys = {}
local running = false
local delay = 1

-- Tab
local Tab = Window:CreateTab("Main", 4483362458)

-- Dropdown pilih skill
Tab:CreateDropdown({
   Name = "Select Skills",
   Options = {"Z","X","C","V","F"},
   CurrentOption = {},
   MultipleOptions = true,
   Callback = function(options)
      selectedKeys = options
   end,
})

-- Slider delay
Tab:CreateSlider({
   Name = "Delay (seconds)",
   Range = {0.1, 3},
   Increment = 0.1,
   CurrentValue = 1,
   Callback = function(value)
      delay = value
   end,
})

-- Toggle Auto Skill
Tab:CreateToggle({
   Name = "Auto Skill",
   CurrentValue = false,
   Callback = function(value)
      running = value
      
      if running then
         spawn(function()
            while running do
               for _, key in pairs(selectedKeys) do
                  vim:SendKeyEvent(true, key, false, game)
                  task.wait(0.1)
                  vim:SendKeyEvent(false, key, false, game)
               end
               task.wait(delay)
            end
         end)
      end
   end,
})
