local player = game.Players.LocalPlayer

print("Halo, " .. Dnx.Nim)

local Players = game:GetService("Players")
local player = Players.LocalPlayer

local gui = Instance.new("ScreenGui")
gui.Name = "MyGUI"
gui.Parent = player:WaitForChild("PlayerGui")

local button = Instance.new("TextButton")
button.Size = UDim2.new(0, 200, 0, 50)
button.Position = UDim2.new(0.5, -100, 0.5, -25)
button.Text = "Klik Saya"
button.Parent = gui

button.MouseButton1Click:Connect(function()
	print("Tombol berhasil diklik!")
	button.Text = "Berhasil!"
end)

local Players = game:GetService("Players")
local player = Players.LocalPlayer

local gui = Instance.new("ScreenGui")
gui.Name = "MyAdminGUI"
gui.ResetOnSpawn = false
gui.Parent = player:WaitForChild("PlayerGui")

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 220, 0, 230)
frame.Position = UDim2.new(0, 20, 0.5, -115)
frame.Parent = gui

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 40)
title.Text = "MY ADMIN GUI"
title.TextScaled = true
title.Parent = frame

local function createButton(text, y)
    local button = Instance.new("TextButton")
    button.Size = UDim2.new(0.85, 0, 0, 45)
    button.Position = UDim2.new(0.075, 0, 0, y)
    button.Text = text
    button.TextScaled = true
    button.Parent = frame
    return button
end

local speedButton = createButton("Speed", 50)
local jumpButton = createButton("Jump", 105)
local resetButton = createButton("Reset", 160)

local function getCharacter()
    return player.Character or player.CharacterAdded:Wait()
end

speedButton.MouseButton1Click:Connect(function()
    local humanoid = getCharacter():FindFirstChildOfClass("Humanoid")
    if humanoid then
        humanoid.WalkSpeed = 50
    end
end)

jumpButton.MouseButton1Click:Connect(function()
    local humanoid = getCharacter():FindFirstChildOfClass("Humanoid")
    if humanoid then
        humanoid.JumpPower = 100
    end
end)

resetButton.MouseButton1Click:Connect(function()
    local humanoid = getCharacter():FindFirstChildOfClass("Humanoid")
    if humanoid then
        humanoid.WalkSpeed = 16
        humanoid.JumpPower = 50
    end
end)

local Players = game:GetService("Players")
local player = Players.LocalPlayer

local gui = Instance.new("ScreenGui")
gui.Name = "MyAdminGUI"
gui.ResetOnSpawn = false
gui.Parent = player:WaitForChild("PlayerGui")

-- Tombol buka/tutup
local openButton = Instance.new("TextButton")
openButton.Size = UDim2.new(0, 100, 0, 40)
openButton.Position = UDim2.new(0, 15, 0, 15)
openButton.Text = "OPEN GUI"
openButton.Parent = gui

-- Panel utama
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 240, 0, 300)
frame.Position = UDim2.new(0, 15, 0.5, -150)
frame.Visible = true
frame.Parent = gui

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 45)
title.Text = "MY ADMIN GUI"
title.TextScaled = true
title.Parent = frame

local function makeButton(text, y)
	local button = Instance.new("TextButton")
	button.Size = UDim2.new(0.85, 0, 0, 45)
	button.Position = UDim2.new(0.075, 0, 0, y)
	button.Text = text
	button.TextScaled = true
	button.Parent = frame
	return button
end

local speed = makeButton("Speed", 55)
local jump = makeButton("Jump", 110)
local heal = makeButton("Heal", 165)
local reset = makeButton("Reset", 220)

local function humanoid()
	local character = player.Character or player.CharacterAdded:Wait()
	return character:FindFirstChildOfClass("Humanoid")
end

speed.MouseButton1Click:Connect(function()
	local h = humanoid()
	if h then
		h.WalkSpeed = 50
	end
end)

jump.MouseButton1Click:Connect(function()
	local h = humanoid()
	if h then
		h.JumpPower = 100
	end
end)

heal.MouseButton1Click:Connect(function()
	local h = humanoid()
	if h then
		h.Health = h.MaxHealth
	end
end)

reset.MouseButton1Click:Connect(function()
	local h = humanoid()
	if h then
		h.WalkSpeed = 16
		h.JumpPower = 50
	end
end)

openButton.MouseButton1Click:Connect(function()
	frame.Visible = not frame.Visible
	openButton.Text = frame.Visible and "CLOSE GUI" or "OPEN GUI"
end)

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")

local player = Players.LocalPlayer

-- GANTI dengan UserId kamu
local ADMIN_IDS = {
	[kecap, trojan] = true,
}

if not ADMIN_IDS[player.UserId] then
	return
end

local gui = Instance.new("ScreenGui")
gui.Name = "AdminGUI"
gui.ResetOnSpawn = false
gui.Parent = player:WaitForChild("PlayerGui")

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 250, 0, 330)
frame.Position = UDim2.new(0, 20, 0.5, -165)
frame.Parent = gui

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 45)
title.Text = "MY ADMIN PANEL"
title.TextScaled = true
title.Parent = frame

local function button(text, y)
	local b = Instance.new("TextButton")
	b.Size = UDim2.new(0.85, 0, 0, 42)
	b.Position = UDim2.new(0.075, 0, 0, y)
	b.Text = text
	b.TextScaled = true
	b.Parent = frame
	return b
end

local speed = button("Speed", 55)
local jump = button("Jump", 105)
local heal = button("Heal", 155)
local fly = button("Fly: OFF", 205)
local noclip = button("Noclip: OFF", 255)

local flying = false
local noclipEnabled = false
local flyConnection

local function getCharacter()
	return player.Character or player.CharacterAdded:Wait()
end

speed.MouseButton1Click:Connect(function()
	local h = getCharacter():FindFirstChildOfClass("Humanoid")
	if h then
		h.WalkSpeed = 50
	end
end)

jump.MouseButton1Click:Connect(function()
	local h = getCharacter():FindFirstChildOfClass("Humanoid")
	if h then
		h.JumpPower = 100
	end
end)

heal.MouseButton1Click:Connect(function()
	local h = getCharacter():FindFirstChildOfClass("Humanoid")
	if h then
		h.Health = h.MaxHealth
	end
end)

fly.MouseButton1Click:Connect(function()
	flying = not flying
	fly.Text = flying and "Fly: ON" or "Fly: OFF"

	if flyConnection then
		flyConnection:Disconnect()
		flyConnection = nil
	end

	if flying then
		flyConnection = RunService.RenderStepped:Connect(function()
			local character = getCharacter()
			local root = character:FindFirstChild("HumanoidRootPart")

			if root then
				root.AssemblyLinearVelocity =
					workspace.CurrentCamera.CFrame.LookVector * 50
			end
		end)
	end
end)

noclip.MouseButton1Click:Connect(function()
	noclipEnabled = not noclipEnabled
	noclip.Text = noclipEnabled and "Noclip: ON" or "Noclip: OFF"

	if noclipEnabled then
		RunService.Stepped:Connect(function()
			if not noclipEnabled then return end

			local character = getCharacter()

			for _, part in ipairs(character:GetDescendants()) do
				if part:IsA("BasePart") then
					part.CanCollide = false
				end
			end
		end)
	end
end)

local Players = game:GetService("Players")

local ADMINS = {
	[kecap, trojan] = true, -- ganti dengan UserId kamu
}

local function isAdmin(player)
	return ADMINS[player.UserId] == true
end

local function getHumanoid(player)
	local character = player.Character
	if not character then return nil end
	return character:FindFirstChildOfClass("Humanoid")
end

local function findPlayer(name)
	name = string.lower(name)

	for _, player in ipairs(Players:GetPlayers()) do
		if string.sub(string.lower(player.Name), 1, #name) == name then
			return player
		end
	end

	return nil
end

local function executeCommand(sender, message)
	if not isAdmin(sender) then
		return
	end

	local args = string.split(message, " ")
	local command = string.lower(args[1] or "")

	if command == "/speed" then
		local target = findPlayer(args[2] or sender.Name)
		local amount = tonumber(args[3]) or 50

		if target then
			local humanoid = getHumanoid(target)
			if humanoid then
				humanoid.WalkSpeed = math.clamp(amount, 0, 100)
			end
		end

	elseif command == "/jump" then
		local target = findPlayer(args[2] or sender.Name)
		local amount = tonumber(args[3]) or 100

		if target then
			local humanoid = getHumanoid(target)
			if humanoid then
				humanoid.JumpPower = math.clamp(amount, 0, 200)
			end
		end

	elseif command == "/heal" then
		local target = findPlayer(args[2] or sender.Name)

		if target then
			local humanoid = getHumanoid(target)
			if humanoid then
				humanoid.Health = humanoid.MaxHealth
			end
		end

	elseif command == "/reset" then
		local target = findPlayer(args[2] or sender.Name)

		if target then
			target:LoadCharacter()
		end

	elseif command == "/kick" then
		local target = findPlayer(args[2] or "")

		if target and target ~= sender then
			target:Kick("Kicked by an administrator.")
		end
	end
end

Players.PlayerAdded:Connect(function(player)
	player.Chatted:Connect(function(message)
		executeCommand(player, message)
	end)
end)

/speed
/speed PlayerName 80
/jump PlayerName 12
/heal PlayerName
/reset PlayerName
/kick PlayerName
AdminCommand
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local AdminCommand = ReplicatedStorage:WaitForChild("AdminCommand")

AdminCommand.OnServerEvent:Connect(function(player, command, targetName, value)
	if not isAdmin(player) then
		return
	end

	local target = player

	if targetName and targetName ~= "" then
		target = findPlayer(targetName)
	end

	if not target then
		return
	end

	local humanoid = getHumanoid(target)
	if not humanoid then
		return
	end

	if command == "Speed" then
		humanoid.WalkSpeed = math.clamp(tonumber(value) or 50, 0, 100)

	elseif command == "Jump" then
		humanoid.JumpPower = math.clamp(tonumber(value) or 100, 0, 200)

	elseif command == "Heal" then
		humanoid.Health = humanoid.MaxHealth

	elseif command == "Reset" then
		target:LoadCharacter()
	end
end)

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local AdminCommand = ReplicatedStorage:WaitForChild("AdminCommand")

local gui = script.Parent

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 250, 0, 280)
frame.Position = UDim2.new(0, 20, 0.5, -140)
frame.Parent = gui

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 45)
title.Text = "ADMIN PANEL"
title.TextScaled = true
title.Parent = frame

local function createButton(text, y)
	local button = Instance.new("TextButton")
	button.Size = UDim2.new(0.8, 0, 0, 40)
	button.Position = UDim2.new(0.1, 0, 0, y)
	button.Text = text
	button.TextScaled = true
	button.Parent = frame

	return button
end

local speed = createButton("SPEED", 55)
local jump = createButton("JUMP", 100)
local heal = createButton("HEAL", 145)
local reset = createButton("RESET", 190)

speed.MouseButton1Click:Connect(function()
	AdminCommand:FireServer("Speed", "", 50)
end)

jump.MouseButton1Click:Connect(function()
	AdminCommand:FireServer("Jump", "", 100)
end)

heal.MouseButton1Click:Connect(function()
	AdminCommand:FireServer("Heal", "")
end)

reset.MouseButton1Click:Connect(function()
	AdminCommand:FireServer("Reset", "")
end)




