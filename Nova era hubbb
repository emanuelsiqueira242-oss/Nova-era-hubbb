--=====================================================
-- NOVA ERA HUB | LOGGER DISCORD (FIX)
--=====================================================

if not game:IsLoaded() then game.Loaded:Wait() end

local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local HttpService = game:GetService("HttpService")
local MarketplaceService = game:GetService("MarketplaceService")

local lp = Players.LocalPlayer

-- Proteção contra execução dupla
if getgenv().NovaEraLogged then return end
getgenv().NovaEraLogged = true

-- WEBHOOK
local WEBHOOK_URL = "https://discord.com/api/webhooks/1454599557416616017/13w-FKs234OFwrp9eeEK5SpiIHvb1BzfPEA11jrCSenJdso99XKdEI2joCRKgSXiz_Gf"

-- Detectar request
local requestFunc =
    request or http_request or syn and syn.request or fluxus and fluxus.request

if not requestFunc then
    warn("[NOVA ERA HUB] Executor sem suporte a request")
    return
end

-- Dispositivo
local device = "Desconhecido"
if UserInputService.TouchEnabled and not UserInputService.KeyboardEnabled then
    device = "📱 Mobile"
elseif UserInputService.KeyboardEnabled then
    device = "💻 PC"
elseif UserInputService.GamepadEnabled then
    device = "🎮 Console"
end

-- Executor
local executor = "Desconhecido"
pcall(function()
    if identifyexecutor then
        executor = identifyexecutor()
    elseif getexecutorname then
        executor = getexecutorname()
    end
end)

-- Nome do jogo (SAFE)
local gameName = "Desconhecido"
pcall(function()
    gameName = MarketplaceService:GetProductInfo(game.PlaceId).Name
end)

-- Payload
local payload = {
    username = "NOVA ERA HUB LOGGER",
    embeds = {{
        title = "🚀 Nova Execução Detectada",
        color = 65280,
        fields = {
            { name = "👤 Jogador", value = lp.Name, inline = true },
            { name = "🆔 UserId", value = tostring(lp.UserId), inline = true },
            { name = "🎮 Jogo", value = gameName, inline = false },
            { name = "🌍 JobId", value = game.JobId, inline = false },
            { name = "📱 Dispositivo", value = device, inline = true },
            { name = "🧠 Executor", value = executor, inline = true }
        },
        footer = {
            text = "Nova Era Hub • " .. os.date("%d/%m/%Y %H:%M:%S")
        }
    }}
}

-- Enviar
requestFunc({
    Url = WEBHOOK_URL,
    Method = "POST",
    Headers = {
        ["Content-Type"] = "application/json"
    },
    Body = HttpService:JSONEncode(payload)
})

--=========================--
--      REDZLIB V5         --
--=========================--
local redzlib = loadstring(game:HttpGet(
    "https://raw.githubusercontent.com/tlredz/Library/refs/heads/main/V5/Source.lua"
))()

local Window = redzlib:MakeWindow({
    Title = "Nova era hub | Brookhaven 🏡",
    SubTitle = "by cabuloso",
    SaveFolder = "Nova era hub"
})

--=========================--
--  BOTÃO DE MINIMIZAR     --
--=========================--
Window:AddMinimizeButton({
    Button = { 
        Image = "rbxassetid://125935053766925",
        Size = UDim2.fromOffset(60, 60),
        BackgroundTransparency = 0 
    },
    Corner = { CornerRadius = UDim.new(0, 6) }
})

--=========================--
--       SERVIÇOS          --
--=========================--
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local LocalPlayer = Players.LocalPlayer

--=========================--
--       ABA: CREDITS      --
--=========================--
local CREDITS = Window:MakeTab({"CREDITS", "alert"})

CREDITS:AddDiscordInvite({
    Name = "NOVA ERA Hub Discord",
    Description = "Entre no Discord oficial do NOVA ERA HUB",
    Logo = "rbxassetid://125935053766925",
    Invite = "https://discord.gg/ARHa3Dnr",
})

CREDITS:AddSection({"Criadores"})
CREDITS:AddParagraph({"Cabuloso"})
CREDITS:AddParagraph({"Dark_edu"})
CREDITS:AddParagraph({""})

--=========================--
-- Ping em tempo real
--=========================--
local pingParagraph = CREDITS:AddParagraph({"Ping", "Calculando..."})
task.spawn(function()
    while task.wait(1) do
        local ping = math.floor(LocalPlayer:GetNetworkPing() * 1000)
        pingParagraph:SetDesc(ping .. " ms")
    end
end)

--=========================--
-- Informações do Jogador
--=========================--
CREDITS:AddSection({"Informações do Jogador"})
CREDITS:AddParagraph({"Seu Nome", LocalPlayer.Name})
CREDITS:AddParagraph({"Display Name", LocalPlayer.DisplayName})

local userIdParagraph = CREDITS:AddParagraph({
    "User ID",
    tostring(LocalPlayer.UserId)
})

CREDITS:AddButton({
    Name = "📋 Copiar User ID",
    Callback = function()
        if setclipboard then
            setclipboard(tostring(LocalPlayer.UserId))
            redzlib:Notify({
                Title = "Copiado",
                Description = "User ID copiado com sucesso",
                Duration = 2
            })
        end
    end
})

--=========================--
-- Código do Jogo (PlaceId)
--=========================--
local placeIdParagraph = CREDITS:AddParagraph({
    "Código do Jogo",
    tostring(game.PlaceId)
})

CREDITS:AddButton({
    Name = "📋 Copiar Código do Jogo",
    Callback = function()
        if setclipboard then
            setclipboard(tostring(game.PlaceId))
            redzlib:Notify({
                Title = "Copiado",
                Description = "Código do jogo copiado",
                Duration = 2
            })
        end
    end
})

--=========================--
-- Sobre
--=========================--
CREDITS:AddSection({"Sobre"})
CREDITS:AddParagraph({"Última Atualização", os.date("%d/%m/%Y")})

--=========================--
-- FPS real (sem bug)
--=========================--
local fpsParagraph = CREDITS:AddParagraph({"FPS", "Calculando..."})
task.spawn(function()
    local last = tick()
    while task.wait(0.3) do
        local now = tick()
        local fps = math.floor(1 / (now - last))
        last = now
        fpsParagraph:SetDesc(fps .. " FPS")
    end
end)
--=========================--
--      ABA: RAINBOW       --
--=========================--
local RainbowTab = Window:MakeTab({"RGB", "brush"})

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local LocalPlayer = Players.LocalPlayer

local RE = ReplicatedStorage:WaitForChild("RE")

local Rainbow = {
    Name = false,
    Bio = false,
    Hair = false,
    Body = false,
    Head = false,
    Speed = 1
}

RainbowTab:AddSection({"RGB Brookhaven"})

--=========================--
-- Toggles
--=========================--
RainbowTab:AddToggle({
    Name = "Nome RGB (RP Name)",
    Default = false,
    Callback = function(v)
        Rainbow.Name = v
    end
})

RainbowTab:AddToggle({
    Name = "Bio RGB",
    Default = false,
    Callback = function(v)
        Rainbow.Bio = v
    end
})

RainbowTab:AddToggle({
    Name = "Cabelo RGB",
    Default = false,
    Callback = function(v)
        Rainbow.Hair = v
    end
})

RainbowTab:AddToggle({
    Name = "Corpo RGB",
    Default = false,
    Callback = function(v)
        Rainbow.Body = v
    end
})

RainbowTab:AddToggle({
    Name = "Cabeça RGB",
    Default = false,
    Callback = function(v)
        Rainbow.Head = v
    end
})

--=========================--
-- Velocidade
--=========================--
RainbowTab:AddSlider({
    Name = "Velocidade do Rainbow",
    Min = 0.5,
    Max = 10,
    Default = 1,
    Decimal = 1,
    Callback = function(v)
        Rainbow.Speed = v
    end
})

--=========================--
-- Loop RGB
--=========================--
task.spawn(function()
    local hue = 0
    while true do
        RunService.Heartbeat:Wait()
        hue = (hue + 0.003 * Rainbow.Speed) % 1
        local color = Color3.fromHSV(hue, 1, 1)

        -- Nome / Bio (Brookhaven)
        if Rainbow.Name and RE:FindFirstChild("1RPNam1eColo1r") then
            RE["1RPNam1eColo1r"]:FireServer("PickingRPNameColor", color)
        end

        if Rainbow.Bio and RE:FindFirstChild("1RPNam1eColo1r") then
            RE["1RPNam1eColo1r"]:FireServer("PickingRPBioColor", color)
        end

        -- Personagem
        if LocalPlayer.Character then
            for _, v in ipairs(LocalPlayer.Character:GetChildren()) do
                if Rainbow.Body and v:IsA("BasePart") and v.Name ~= "HumanoidRootPart" then
                    v.Color = color
                end

                if Rainbow.Head and v.Name == "Head" then
                    v.Color = color
                end

                if Rainbow.Hair and v:IsA("Accessory") and v:FindFirstChild("Handle") then
                    v.Handle.Color = color
                end
            end
        end
    end
end)

RainbowTab:AddSection({"Info"})
RainbowTab:AddParagraph({
    "Modo RGB",
    "Funciona para todos verem (Brookhaven RP)"
})
--=========================--
--   ABA: TELEPORTES       --
--=========================--
local Fun = Window:MakeTab({"TELEPORTES", "fun"})
Fun:AddParagraph({"LUGARES DO BROOKHAVEN", "Lista completa dos locais para teleporte"})

local teleportList = {
    {Name = "Início", Position = Vector3.new(0, 5, 0)},
    {Name = "Esconderijo", Position = Vector3.new(457.5, -72.5, 112.7)},
    {Name = "Mecânica", Position = Vector3.new(-41.2, 2.6, -376.8)},
    {Name = "Esconderijo Agency do Posto", Position = Vector3.new(182.6, 2.5, -412.1)},
    {Name = "Posto", Position = Vector3.new(130.5, 2.5, -328.0)},
    {Name = "Shopping", Position = Vector3.new(154.1, 2.7, -145.4)},
    {Name = "Super Mercado", Position = Vector3.new(5.7, 2.6, -117.0)},
    {Name = "Escola", Position = Vector3.new(-291.4, 5.8, 216.7)}
}

local SelectedTeleport = teleportList[1].Name
Fun:AddDropdown({
    Name = "Selecionar Local",
    Options = (function()
        local t = {}
        for _, v in ipairs(teleportList) do table.insert(t, v.Name) end
        return t
    end)(),
    Default = SelectedTeleport,
    Callback = function(v) SelectedTeleport = v end
})

Fun:AddButton({"Teleportar", function()
    local lp = game.Players.LocalPlayer
    local targetData
    for _, v in ipairs(teleportList) do
        if v.Name == SelectedTeleport then targetData = v break end
    end
    if targetData and lp.Character and lp.Character:FindFirstChild("HumanoidRootPart") then
        lp.Character.HumanoidRootPart.CFrame = CFrame.new(targetData.Position)
        redzlib:Notification({
            Title = "Teleport",
            Description = "Você foi teleportado para: " .. targetData.Name,
            Duration = 3
        })
    end
end})

--=========================--
--   ABA TROLL COMPLETA    --
--=========================--
local Troll = Window:MakeTab({"TROLL", "rbxassetid://140731226103831"})
Troll:AddSection({"Jogadores do servidor"})

local lp = game.Players.LocalPlayer

local function getPlayers()
    local list = {}
    for _, p in ipairs(game.Players:GetPlayers()) do
        table.insert(list, p.Name)
    end
    return list
end

local SelectedPlayer = nil
local PlayerDropdown = Troll:AddDropdown({
    Name = "Selecione um jogador",
    Options = getPlayers(),
    Default = getPlayers()[1],
    Callback = function(v) SelectedPlayer = v end
})

local function refreshPlayers()
    local players = getPlayers()
    PlayerDropdown:Refresh(players, true)
    SelectedPlayer = players[1]
end

Troll:AddButton({"Atualizar lista", refreshPlayers})
game.Players.PlayerAdded:Connect(refreshPlayers)
game.Players.PlayerRemoving:Connect(refreshPlayers)

-- Spectar jogador
Troll:AddButton({"Spectar Jogador", function()
    if not SelectedPlayer then return end
    local plr = game.Players:FindFirstChild(SelectedPlayer)
    if plr and plr.Character and plr.Character:FindFirstChild("Humanoid") then
        workspace.CurrentCamera.CameraSubject = plr.Character.Humanoid
    end
end})

-- Parar Spectar
Troll:AddButton({"Parar Spectar", function()
    if lp.Character and lp.Character:FindFirstChild("Humanoid") then
        workspace.CurrentCamera.CameraSubject = lp.Character.Humanoid
    end
end})

-- Teleportar até jogador
Troll:AddButton({"Teleportar até jogador", function()
    if not SelectedPlayer then return end
    local plr = game.Players:FindFirstChild(SelectedPlayer)
    if plr and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") and lp.Character then
        lp.Character.HumanoidRootPart.CFrame = plr.Character.HumanoidRootPart.CFrame * CFrame.new(0,2,0)
    end
end})

-- Get Sofá
Troll:AddButton({"Get Sofá", function()
    if lp.Character and lp.Character:FindFirstChild("HumanoidRootPart") then
        lp.Character.HumanoidRootPart.CFrame = CFrame.new(-82.4, 21, -129.4)
        redzlib:Notification({Title = "Get Sofá", Description = "Você foi teleportado para o sofá!", Duration = 3})
    end
end})

-- Seguir jogador
local FollowEnabled = false
Troll:AddToggle({Name = "Seguir jogador", Default = false, Callback = function(v)
    FollowEnabled = v
    task.spawn(function()
        while FollowEnabled do
            if SelectedPlayer then
                local plr = game.Players:FindFirstChild(SelectedPlayer)
                if plr and plr.Character and lp.Character then
                    local myHRP = lp.Character:FindFirstChild("HumanoidRootPart")
                    local targetHRP = plr.Character:FindFirstChild("HumanoidRootPart")
                    if myHRP and targetHRP then
                        myHRP.CFrame = targetHRP.CFrame * CFrame.new(1.3,0,0)
                    end
                end
            end
            task.wait(0.05)
        end
    end)
end})

-- Sliders
local flingPower = 200
Troll:AddSlider({Name = "Potência Fling", Min=50, Max=1000, Default=flingPower, Decimal=0, Callback=function(v) flingPower=v end})
local superBugPower = 50
Troll:AddSlider({Name = "Força Super Bug", Min=10, Max=500, Default=superBugPower, Decimal=0, Callback=function(v) superBugPower=v end})

-- Super Bug Troll
local GuardarEnabled = false
local spinningForce, moveForce
Troll:AddToggle({Name = "Super Bug Troll", Default = false, Callback = function(v)
    GuardarEnabled = v
    if not v then if spinningForce then spinningForce:Destroy() end if moveForce then moveForce:Destroy() end return end
    task.spawn(function()
        local hrp = lp.Character and lp.Character:FindFirstChild("HumanoidRootPart")
        if not hrp then return end
        spinningForce = Instance.new("BodyAngularVelocity")
        spinningForce.AngularVelocity = Vector3.new(0,superBugPower,0)
        spinningForce.MaxTorque = Vector3.new(1e9,1e9,1e9)
        spinningForce.Parent = hrp
        moveForce = Instance.new("BodyVelocity")
        moveForce.MaxForce = Vector3.new(1e9,1e9,1e9)
        moveForce.Parent = hrp
        while GuardarEnabled do
            moveForce.Velocity = Vector3.new(math.random(-superBugPower,superBugPower),
                                            math.random(-superBugPower,superBugPower),
                                            math.random(-superBugPower,superBugPower))
            task.wait(0.1)
        end
    end)
end})

-- Fling Jogador
local FlingEnabled = false
Troll:AddToggle({Name = "Fling Jogador", Default = false, Callback = function(state)
    FlingEnabled = state
    task.spawn(function()
        while FlingEnabled do
            if SelectedPlayer then
                local plr = game.Players:FindFirstChild(SelectedPlayer)
                if plr and plr.Character and lp.Character then
                    local targetHRP = plr.Character:FindFirstChild("HumanoidRootPart")
                    local myHRP = lp.Character:FindFirstChild("HumanoidRootPart")
                    if targetHRP and myHRP then
                        local bv = Instance.new("BodyVelocity")
                        bv.MaxForce = Vector3.new(1e9,1e9,1e9)
                        bv.Velocity = (targetHRP.Position - myHRP.Position).Unit * flingPower
                        bv.Parent = myHRP
                        task.wait(0.1)
                        bv:Destroy()
                    end
                end
            end
            task.wait(0.1)
        end
    end)
end})

-- Bring ao sentar
local BringEnabled = false
Troll:AddToggle({Name = "Bring ao Sentar", Default = false, Callback = function(state)
    BringEnabled = state
    task.spawn(function()
        while BringEnabled do
            if SelectedPlayer then
                local plr = game.Players:FindFirstChild(SelectedPlayer)
                if plr and plr.Character and lp.Character then
                    local targetHumanoid = plr.Character:FindFirstChild("Humanoid")
                    local targetHRP = plr.Character:FindFirstChild("HumanoidRootPart")
                    local myHRP = lp.Character:FindFirstChild("HumanoidRootPart")
                    if targetHumanoid and targetHRP and myHRP and targetHumanoid.Sit then
                        targetHRP.CFrame = myHRP.CFrame
                    end
                end
            end
            task.wait(0.1)
        end
    end)
end})

-- SitHead Troll
Troll:AddButton({"SitHead", function()
    if not SelectedPlayer then return end
    local plr = game.Players:FindFirstChild(SelectedPlayer)
    if plr and plr.Character and plr.Character:FindFirstChild("HumanoidRootPart") and plr.Character:FindFirstChild("Head") then
        local hrp = plr.Character.HumanoidRootPart
        local head = plr.Character.Head
        hrp.CFrame = CFrame.new(hrp.Position.X, hrp.Position.Y - 2, hrp.Position.Z)
        head.CFrame = hrp.CFrame * CFrame.new(0,-1,0)
        redzlib:Notification({Title="SitHead", Description="Cabeça do jogador abaixada!", Duration=3})
    end
end})

local Tab = Window:MakeTab({"Script", "paper"})

Tab:AddButton({ Name = "fly v1",
    Callback = function()
 loadstring(game:HttpGet("https://pastebin.com/raw/71PGKEwU"))()
    end
}) 

local OP = Window:MakeTab({"OP", "disc"})

OP:AddSection({Name = "Player"})

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local lp = Players.LocalPlayer

-- SPEED
OP:AddSlider({
    Name = "Speed",
    Min = 16,
    Max = 190,
    Default = 16,
    Increment = 1,
    Callback = function(v)
        local hum = lp.Character and lp.Character:FindFirstChildOfClass("Humanoid")
        if hum then hum.WalkSpeed = v end
    end
})

-- JUMP
OP:AddSlider({
    Name = "Jump Power",
    Min = 50,
    Max = 190,
    Default = 50,
    Increment = 1,
    Callback = function(v)
        local hum = lp.Character and lp.Character:FindFirstChildOfClass("Humanoid")
        if hum then hum.JumpPower = v end
    end
})

--=========================
-- NOCLIP (SEM LOOP BUG)
--=========================
local Noclip = false
OP:AddToggle({
    Name = "Noclip",
    Default = false,
    Callback = function(v)
        Noclip = v
    end
})

RunService.Stepped:Connect(function()
    if Noclip and lp.Character then
        for _,p in pairs(lp.Character:GetDescendants()) do
            if p:IsA("BasePart") then
                p.CanCollide = false
            end
        end
    end
end)

--=========================
-- INFINITY JUMP
--=========================
local InfJump = false
OP:AddToggle({
    Name = "Infinity Jump",
    Default = false,
    Callback = function(v)
        InfJump = v
    end
})

game:GetService("UserInputService").JumpRequest:Connect(function()
    if InfJump and lp.Character then
        local hum = lp.Character:FindFirstChildOfClass("Humanoid")
        if hum then
            hum:ChangeState(Enum.HumanoidStateType.Jumping)
        end
    end
end)

OP:AddSection({Name = "🚧 Mais em breve..."})
OP:AddSection({Name = "❓ Em desenvolvimento"})
