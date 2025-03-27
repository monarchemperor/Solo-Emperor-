# Solo-Emperor-

local player = game.Players.LocalPlayer
local replicatedStorage = game:GetService("ReplicatedStorage")
local npcTemplate = replicatedStorage:WaitForChild("NPC")
local button = script.Parent

local function spawnNPC()
    local character = player.Character or player.CharacterAdded:Wait()
    if not character then return end  -- Safety check

    local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")
    if not humanoidRootPart then return end  -- Safety check

    local newNPC = npcTemplate:Clone()
    if newNPC.PrimaryPart then
        newNPC.Parent = workspace
        newNPC:SetPrimaryPartCFrame(humanoidRootPart.CFrame * CFrame.new(5, 0, 5))
    else
        warn("NPC model has no PrimaryPart!")
    end
end

button.MouseButton1Click:Connect(spawnNPC)
