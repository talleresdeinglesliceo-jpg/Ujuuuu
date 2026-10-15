local Players = game:GetService("Players")
local TeleportService = game:GetService("TeleportService")
local HttpService = game:GetService("HttpService")
local LocalPlayer = Players.LocalPlayer
local PlayerGui = LocalPlayer:WaitForChild("PlayerGui")

local screenGui = Instance.new("ScreenGui")
screenGui.Name = "DezelikHudGui"
screenGui.ResetOnSpawn = false
screenGui.Parent = PlayerGui

local mainFrame = Instance.new("Frame")
mainFrame.Name = "DezelikHudMain"
mainFrame.Size = UDim2.new(0, 280, 0, 370)
mainFrame.Position = UDim2.new(0.5, -140, 0.22, 0)
mainFrame.BackgroundColor3 = Color3.fromRGB(18, 18, 24)
mainFrame.BorderSizePixel = 0
mainFrame.Active = true
mainFrame.Draggable = true
mainFrame.Parent = screenGui

local mainCorner = Instance.new("UICorner")
mainCorner.CornerRadius = UDim.new(0, 16)
mainCorner.Parent = mainFrame

local mainStroke = Instance.new("UIStroke")
mainStroke.Color = Color3.fromRGB(50, 50, 70)
mainStroke.Thickness = 1.5
mainStroke.Parent = mainFrame

local titleLabel = Instance.new("TextLabel")
titleLabel.Name = "Title"
titleLabel.Size = UDim2.new(1, -20, 0, 24)
titleLabel.Position = UDim2.new(0, 12, 0, 12)
titleLabel.BackgroundTransparency = 1
titleLabel.Text = "PRIVATE SERVER FINDER"
titleLabel.TextColor3 = Color3.fromRGB(220, 220, 240)
titleLabel.TextSize = 13
titleLabel.Font = Enum.Font.GothamBold
titleLabel.TextXAlignment = Enum.TextXAlignment.Left
titleLabel.Parent = mainFrame

local subTitle = Instance.new("TextLabel")
subTitle.Name = "Subtitle"
subTitle.Size = UDim2.new(1, -20, 0, 16)
subTitle.Position = UDim2.new(0, 12, 0, 32)
subTitle.BackgroundTransparency = 1
subTitle.Text = "by Ego"
subTitle.TextColor3 = Color3.fromRGB(120, 120, 150)
subTitle.TextSize = 11
subTitle.Font = Enum.Font.GothamMedium
subTitle.TextXAlignment = Enum.TextXAlignment.Left
subTitle.Parent = mainFrame

local currentServerBox = Instance.new("Frame")
currentServerBox.Size = UDim2.new(1, -24, 0, 36)
currentServerBox.Position = UDim2.new(0, 12, 0, 58)
currentServerBox.BackgroundColor3 = Color3.fromRGB(28, 28, 38)
currentServerBox.BorderSizePixel = 0
currentServerBox.Parent = mainFrame

local boxCorner = Instance.new("UICorner")
boxCorner.CornerRadius = UDim.new(0, 8)
boxCorner.Parent = currentServerBox

local currentServerText = Instance.new("TextLabel")
currentServerText.Size = UDim2.new(1, -16, 1, 0)
currentServerText.Position = UDim2.new(0, 12, 0, 0)
currentServerText.BackgroundTransparency = 1
currentServerText.Text = "Current Server: " .. #Players:GetPlayers() .. " player(s)"
currentServerText.TextColor3 = Color3.fromRGB(50, 205, 50)
currentServerText.TextSize = 12
currentServerText.Font = Enum.Font.GothamBold
currentServerText.TextXAlignment = Enum.TextXAlignment.Left
currentServerText.Parent = currentServerBox

local descLabel = Instance.new("TextLabel")
descLabel.Size = UDim2.new(1, -24, 0, 20)
descLabel.Position = UDim2.new(0, 12, 0, 104)
descLabel.BackgroundTransparency = 1
descLabel.Text = "Set max threshold & click Hop."
descLabel.TextColor3 = Color3.fromRGB(140, 140, 160)
descLabel.TextSize = 11
descLabel.Font = Enum.Font.GothamMedium
descLabel.TextXAlignment = Enum.TextXAlignment.Left
descLabel.Parent = mainFrame

local inputMaxPlayers = Instance.new("TextBox")
inputMaxPlayers.Name = "InputMaxPlayers"
inputMaxPlayers.Size = UDim2.new(1, -24, 0, 38)
inputMaxPlayers.Position = UDim2.new(0, 12, 0, 130)
inputMaxPlayers.BackgroundColor3 = Color3.fromRGB(28, 28, 38)
inputMaxPlayers.PlaceholderText = "Max players (ej: 4)"
inputMaxPlayers.Text = ""
inputMaxPlayers.TextColor3 = Color3.fromRGB(255, 255, 255)
inputMaxPlayers.PlaceholderColor3 = Color3.fromRGB(100, 100, 120)
inputMaxPlayers.TextSize = 13
inputMaxPlayers.Font = Enum.Font.GothamMedium
inputMaxPlayers.ClearTextOnFocus = false
inputMaxPlayers.BorderSizePixel = 0
inputMaxPlayers.Parent = mainFrame

local inputCorner = Instance.new("UICorner")
inputCorner.CornerRadius = UDim.new(0, 8)
inputCorner.Parent = inputMaxPlayers

local hopBtn = Instance.new("TextButton")
hopBtn.Name = "HopButton"
hopBtn.Size = UDim2.new(1, -24, 0, 42)
hopBtn.Position = UDim2.new(0, 12, 0, 180)
hopBtn.BackgroundColor3 = Color3.fromRGB(0, 122, 255)
hopBtn.Text = "HOP SERVER NOW"
hopBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
hopBtn.TextSize = 13
hopBtn.Font = Enum.Font.GothamBold
hopBtn.BorderSizePixel = 0
hopBtn.Parent = mainFrame

local hopCorner = Instance.new("UICorner")
hopCorner.CornerRadius = UDim.new(0, 8)
hopCorner.Parent = hopBtn

local dropdownContainer = Instance.new("Frame")
dropdownContainer.Size = UDim2.new(1, -24, 0, 85)
dropdownContainer.Position = UDim2.new(0, 12, 0, 232)
dropdownContainer.BackgroundTransparency = 1
dropdownContainer.Parent = mainFrame

local searchEggBtn = Instance.new("TextButton")
searchEggBtn.Size = UDim2.new(1, 0, 0, 38)
searchEggBtn.Position = UDim2.new(0, 0, 0, 0)
searchEggBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 38)
searchEggBtn.Text = "▼ SEARCH LARGE EGG"
searchEggBtn.TextColor3 = Color3.fromRGB(255, 200, 50)
searchEggBtn.TextSize = 12
searchEggBtn.Font = Enum.Font.GothamBold
searchEggBtn.BorderSizePixel = 0
searchEggBtn.Parent = dropdownContainer

local seCorner = Instance.new("UICorner")
seCorner.CornerRadius = UDim.new(0, 8)
seCorner.Parent = searchEggBtn

local searchEggContent = Instance.new("Frame")
searchEggContent.Size = UDim2.new(1, 0, 0, 35)
searchEggContent.Position = UDim2.new(0, 0, 0, 42)
searchEggContent.BackgroundColor3 = Color3.fromRGB(22, 22, 30)
searchEggContent.Visible = false
searchEggContent.Parent = dropdownContainer

local secCorner = Instance.new("UICorner")
secCorner.CornerRadius = UDim.new(0, 6)
secCorner.Parent = searchEggContent

local seText = Instance.new("TextLabel")
seText.Size = UDim2.new(1, -10, 1, 0)
seText.Position = UDim2.new(0, 5, 0, 0)
seText.BackgroundTransparency = 1
seText.Text = "Status: Looking for large eggs..."
seText.TextColor3 = Color3.fromRGB(180, 180, 200)
seText.TextSize = 11
seText.Font = Enum.Font.GothamMedium
seText.Parent = searchEggContent

local eggOpen = false
searchEggBtn.MouseButton1Click:Connect(function()
	eggOpen = not eggOpen
	searchEggContent.Visible = eggOpen
	if eggOpen then
		searchEggBtn.Text = "▲ SEARCH LARGE EGG"
		dropdownContainer.Size = UDim2.new(1, -24, 0, 125)
		mainFrame.Size = UDim2.new(0, 280, 0, 410)
	else
		searchEggBtn.Text = "▼ SEARCH LARGE EGG"
		dropdownContainer.Size = UDim2.new(1, -24, 0, 85)
		mainFrame.Size = UDim2.new(0, 280, 0, 370)
	end
end)

local creditsBtn = Instance.new("TextButton")
creditsBtn.Size = UDim2.new(1, 0, 0, 38)
creditsBtn.Position = UDim2.new(0, 0, 0, 43)
creditsBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 38)
creditsBtn.Text = "▼ CREDITS (Ego & Gemini)"
creditsBtn.TextColor3 = Color3.fromRGB(100, 200, 255)
creditsBtn.TextSize = 12
creditsBtn.Font = Enum.Font.GothamBold
creditsBtn.BorderSizePixel = 0
creditsBtn.Parent = dropdownContainer

local crCorner = Instance.new("UICorner")
crCorner.CornerRadius = UDim.new(0, 8)
crCorner.Parent = creditsBtn

local creditsContent = Instance.new("Frame")
creditsContent.Size = UDim2.new(1, 0, 0, 45)
creditsContent.Position = UDim2.new(0, 0, 0, 85)
creditsContent.BackgroundColor3 = Color3.fromRGB(22, 22, 30)
creditsContent.Visible = false
creditsContent.Parent = dropdownContainer

local crcCorner = Instance.new("UICorner")
crcCorner.CornerRadius = UDim.new(0, 6)
crcCorner.Parent = creditsContent

local crText = Instance.new("TextLabel")
crText.Size = UDim2.new(1, -10, 1, 0)
crText.Position = UDim2.new(0, 5, 0, 0)
crText.BackgroundTransparency = 1
crText.Text = "Script created by Ego\nOptimized with Gemini AI"
crText.TextColor3 = Color3.fromRGB(180, 180, 200)
crText.TextSize = 11
crText.Font = Enum.Font.GothamMedium
crText.TextWrapped = true
crText.Parent = creditsContent

local creditsOpen = false
creditsBtn.MouseButton1Click:Connect(function()
	creditsOpen = not creditsOpen
	creditsContent.Visible = creditsOpen
	if creditsOpen then
		creditsBtn.Text = "▲ CREDITS (Ego & Gemini)"
		dropdownContainer.Size = UDim2.new(1, -24, 0, 135)
		mainFrame.Size = UDim2.new(0, 280, 0, 420)
	else
		creditsBtn.Text = "▼ CREDITS (Ego & Gemini)"
		dropdownContainer.Size = UDim2.new(1, -24, 0, 85)
		mainFrame.Size = UDim2.new(0, 280, 0, 370)
	end
end)

local minMaxBtn = Instance.new("TextButton")
minMaxBtn.Name = "MinMaxButton"
minMaxBtn.Size = UDim2.new(0, 24, 0, 24)
minMaxBtn.Position = UDim2.new(1, -32, 0, 12)
minMaxBtn.BackgroundColor3 = Color3.fromRGB(35, 35, 45)
minMaxBtn.Text = "_"
minMaxBtn.TextColor3 = Color3.fromRGB(200, 200, 200)
minMaxBtn.TextSize = 12
minMaxBtn.Font = Enum.Font.GothamBold
minMaxBtn.BorderSizePixel = 0
minMaxBtn.Parent = mainFrame

local minCorner = Instance.new("UICorner")
minCorner.CornerRadius = UDim.new(0, 6)
minCorner.Parent = minMaxBtn

local function fastHop(maxLimit)
	hopBtn.Text = "SEARCHING..."
	hopBtn.BackgroundColor3 = Color3.fromRGB(80, 80, 100)
	
	task.spawn(function()
		local success, result = pcall(function()
			local url = "https://games.roblox.com/v1/games/" .. game.PlaceId .. "/servers/Public?sortOrder=Asc&limit=100"
			return HttpService:JSONDecode(game:HttpGet(url))
		end)
		
		if success and result and result.data then
			local bestServerId = nil
			local lowestPlayers = 999
			local exactMatchFound = false
			
			for _, server in ipairs(result.data) do
				local currentPlayers = server.playing
				local maxPlayersInServer = server.maxPlayers
				
				if currentPlayers < maxPlayersInServer and server.id ~= game.JobId then
					if maxLimit and currentPlayers <= maxLimit then
						if currentPlayers > lowestPlayers or not bestServerId then
							lowestPlayers = currentPlayers
							bestServerId = server.id
							exactMatchFound = true
						end
					else
						if not exactMatchFound and currentPlayers < lowestPlayers then
							lowestPlayers = currentPlayers
							bestServerId = server.id
						end
					end
				end
			end
			
			if bestServerId then
				TeleportService:TeleportToPlaceInstance(game.PlaceId, bestServerId, LocalPlayer)
			else
				TeleportService:Teleport(game.PlaceId, LocalPlayer)
			end
		else
			TeleportService:Teleport(game.PlaceId, LocalPlayer)
		end
	end)
end

hopBtn.MouseButton1Click:Connect(function()
	local targetLimit = tonumber(inputMaxPlayers.Text)
	fastHop(targetLimit)
end)

local isMinimized = false
minMaxBtn.MouseButton1Click:Connect(function()
	if isMinimized then
		isMinimized = false
		currentServerBox.Visible = true
		descLabel.Visible = true
		inputMaxPlayers.Visible = true
		hopBtn.Visible = true
		dropdownContainer.Visible = true
		subTitle.Visible = true
		mainFrame.Size = UDim2.new(0, 280, 0, 370)
		minMaxBtn.Text = "_"
	else
		isMinimized = true
		currentServerBox.Visible = false
		descLabel.Visible = false
		inputMaxPlayers.Visible = false
		hopBtn.Visible = false
		dropdownContainer.Visible = false
		subTitle.Visible = false
		mainFrame.Size = UDim2.new(0, 280, 0, 48)
		minMaxBtn.Text = "+"
	end
end)
