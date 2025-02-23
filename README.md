local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local HttpService = game:GetService("HttpService")

-- Criando GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = LocalPlayer:FindFirstChildOfClass("PlayerGui")

local Frame = Instance.new("Frame")
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
Frame.Size = UDim2.new(0, 300, 0, 250)
Frame.Position = UDim2.new(0.3, 0, 0.3, 0)
Frame.Visible = true

local Title = Instance.new("TextLabel")
Title.Parent = Frame
Title.Text = "FACILITAR FARM DE PEÇA DE ARMA(AWAYS)"
Title.Size = UDim2.new(1, 0, 0, 30)
Title.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Title.TextColor3 = Color3.fromRGB(255, 255, 255)

local MinimizeButton = Instance.new("TextButton")
MinimizeButton.Parent = Frame
MinimizeButton.Text = "-"
MinimizeButton.Size = UDim2.new(0, 30, 0, 30)
MinimizeButton.Position = UDim2.new(1, -35, 0, 0)
MinimizeButton.BackgroundColor3 = Color3.fromRGB(200, 50, 50)

local TeleportFacc = Instance.new("TextButton")
TeleportFacc.Parent = Frame
TeleportFacc.Text = "Teleporte Facc"
TeleportFacc.Size = UDim2.new(1, -10, 0, 50)
TeleportFacc.Position = UDim2.new(0, 5, 0, 50)
TeleportFacc.BackgroundColor3 = Color3.fromRGB(50, 150, 50)

local TeleportPeca = Instance.new("TextButton")
TeleportPeca.Parent = Frame
TeleportPeca.Text = "Teleporte Peça"
TeleportPeca.Size = UDim2.new(1, -10, 0, 50)
TeleportPeca.Position = UDim2.new(0, 5, 0, 110)
TeleportPeca.BackgroundColor3 = Color3.fromRGB(50, 50, 150)

local TeleportFacc2 = Instance.new("TextButton")
TeleportFacc2.Parent = Frame
TeleportFacc2.Text = "Facc 2"
TeleportFacc2.Size = UDim2.new(1, -10, 0, 50)
TeleportFacc2.Position = UDim2.new(0, 5, 0, 170)
TeleportFacc2.BackgroundColor3 = Color3.fromRGB(150, 50, 150)

-- Minimize
local Minimized = false
local MinimizeGUI = Instance.new("TextButton")
MinimizeGUI.Parent = ScreenGui
MinimizeGUI.Text = "Max"
MinimizeGUI.Size = UDim2.new(0, 50, 0, 30)
MinimizeGUI.Position = UDim2.new(0.3, 0, 0.3, 0)
MinimizeGUI.BackgroundColor3 = Color3.fromRGB(200, 200, 50)
MinimizeGUI.Visible = false

MinimizeButton.MouseButton1Click:Connect(function()
    Minimized = not Minimized
    Frame.Visible = not Minimized
    MinimizeGUI.Visible = Minimized
end)

MinimizeGUI.MouseButton1Click:Connect(function()
    Minimized = false
    Frame.Visible = true
    MinimizeGUI.Visible = false
end)

-- Função de Teleporte
local function TeleportTo(Position)
    local Character = LocalPlayer.Character
    if Character and Character:FindFirstChild("HumanoidRootPart") then
        Character:WaitForChild("HumanoidRootPart").CFrame = CFrame.new(Position)
    else
        warn("Personagem não encontrado!")
    end
end

TeleportFacc.MouseButton1Click:Connect(function()
    print("Teleportando para Facc...")
    TeleportTo(Vector3.new(-668.4, 23.5, -117.7))
end)

TeleportPeca.MouseButton1Click:Connect(function()
    print("Teleportando para Peça...")
    TeleportTo(Vector3.new(-1113.4, 28.0, -508.6))
end)

TeleportFacc2.MouseButton1Click:Connect(function()
    print("Teleportando para Facc 2...")
    TeleportTo(Vector3.new(260.8, 23.5, 529.3))
end)

-- Executar Fly
local success, err = pcall(function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/XNEOFF/FlyGuiV3/main/FlyGuiV3.txt"))()
end)
if not success then
    warn("Erro ao carregar o script de voo:", err)
end
