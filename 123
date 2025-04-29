local UserInputService = game:GetService("UserInputService")
local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Saber_RS = ReplicatedStorage:WaitForChild("Saber_RS")
local Remotes = Saber_RS:WaitForChild("RemoteEvents")
local LightSaberEvt = Remotes:WaitForChild("LightsaberEvent30")

local args = {
[1] = "BlockRegen",
[2] = 2
}

local Player = Players.LocalPlayer
local Character = Player.Character or Player.CharacterAdded:Wait()

Player.CharacterAdded:Connect(function(char)
Character = char
end)

_G.toggle = false

UserInputService.InputBegan:Connect(function(input, gpe)
if not gpe then
if input.KeyCode == Enum.KeyCode.F5 then
_G.toggle = not _G.toggle
print("Force regen toggled:", _G.toggle)
end
end
end)

coroutine.wrap(function()
while true do
if _G.toggle and Character then
local Humanoid = Character:FindFirstChild("Humanoid")
if Humanoid and Humanoid.Health > 0 then
local Force = Character:FindFirstChild("ForceValue")
if Force and Force.Value <= 10 then
Force.Value = 100
end
end
end
task.wait()
end
end)()

coroutine.wrap(function()
while true do
if Character then
local Humanoid = Character:FindFirstChild("Humanoid")
if Humanoid and Humanoid.Health > 0 then
LightSaberEvt:FireServer(unpack(args))
end
end
task.wait()
end
end)()
