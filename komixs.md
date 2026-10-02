-- SCRIPT BY KOMIXS v4.0 | FTAP MEGA HUB
print("[SCRIPT BY KOMIXS] Загрузка...")

local Players = game:GetService("Players")
local Workspace = game:GetService("Workspace")
local UIS = game:GetService("UserInputService")
local RS = game:GetService("RunService")
local TS = game:GetService("TweenService")
local Lighting = game:GetService("Lighting")
local LP = Players.LocalPlayer
local Cam = Workspace.CurrentCamera

for _, g in ipairs(LP.PlayerGui:GetChildren()) do
    if g.Name:find("KOMIXS") then g:Destroy() end
end

-- HUD
local HUD = Instance.new("ScreenGui", LP:WaitForChild("PlayerGui"))
HUD.Name = "KOMIXS_HUD"
HUD.ResetOnSpawn = false
local HF = Instance.new("Frame", HUD)
HF.Size = UDim2.new(0, 170, 0, 56)
HF.Position = UDim2.new(1, -185, 0, 45)
HF.BackgroundColor3 = Color3.fromRGB(15, 15, 22)
HF.BackgroundTransparency = 0.25
HF.BorderSizePixel = 0
Instance.new("UICorner", HF).CornerRadius = UDim.new(0, 8)
local HS = Instance.new("UIStroke", HF)
HS.Color = Color3.fromRGB(255, 140, 0)
HS.Thickness = 1.5
HS.Transparency = 0.3

local Brand = Instance.new("TextLabel", HF)
Brand.Size = UDim2.new(1, -10, 0, 16)
Brand.Position = UDim2.new(0, 5, 0, 2)
Brand.BackgroundTransparency = 1
Brand.Text = "⚡ SCRIPT BY KOMIXS"
Brand.TextColor3 = Color3.fromRGB(255, 215, 0)
Brand.Font = Enum.Font.GothamBold
Brand.TextSize = 10
Brand.TextXAlignment = Enum.TextXAlignment.Left

local FPSL = Instance.new("TextLabel", HF)
FPSL.Size = UDim2.new(1, -10, 0, 16)
FPSL.Position = UDim2.new(0, 5, 0, 19)
FPSL.BackgroundTransparency = 1
FPSL.Text = "🎮 FPS: --"
FPSL.TextColor3 = Color3.fromRGB(0, 255, 100)
FPSL.Font = Enum.Font.GothamBold
FPSL.TextSize = 11
FPSL.TextXAlignment = Enum.TextXAlignment.Left

local PingL = Instance.new("TextLabel", HF)
PingL.Size = UDim2.new(1, -10, 0, 16)
PingL.Position = UDim2.new(0, 5, 0, 36)
PingL.BackgroundTransparency = 1
PingL.Text = "📡 Ping: --"
PingL.TextColor3 = Color3.fromRGB(100, 200, 255)
PingL.Font = Enum.Font.GothamBold
PingL.TextSize = 11
PingL.TextXAlignment = Enum.TextXAlignment.Left

local fr, lt = 0, tick()
RS.RenderStepped:Connect(function()
    fr = fr + 1
    if tick() - lt >= 1 then
        local fps = math.floor(fr / (tick() - lt))
        fr, lt = 0, tick()
        FPSL.Text = "🎮 FPS: " .. fps
        FPSL.TextColor3 = fps >= 50 and Color3.fromRGB(0, 255, 100) or fps >= 30 and Color3.fromRGB(255, 200, 0) or Color3.fromRGB(255, 60, 60)
    end
end)

task.spawn(function()
    while true do
        pcall(function()
            local p = math.floor(LP:GetNetworkPing() * 1000)
            PingL.Text = "📡 Ping: " .. p .. " ms"
            PingL.TextColor3 = p < 80 and Color3.fromRGB(0, 255, 100) or p < 150 and Color3.fromRGB(255, 200, 0) or Color3.fromRGB(255, 60, 60)
        end)
        task.wait(0.5)
    end
end)

-- GUI
local GUI = Instance.new("ScreenGui", LP:WaitForChild("PlayerGui"))
GUI.Name = "KOMIXS_Hub"
GUI.ResetOnSpawn = false
GUI.IgnoreGuiInset = true

local Main = Instance.new("Frame", GUI)
Main.Size = UDim2.new(0, 520, 0, 380)
Main.Position = UDim2.new(0, -600, 0.5, -190)
Main.BackgroundColor3 = Color3.fromRGB(15, 15, 22)
Main.BackgroundTransparency = 0.05
Main.BorderSizePixel = 0
Main.Active = true
Main.Draggable = true
Instance.new("UICorner", Main).CornerRadius = UDim.new(0, 14)
local MS = Instance.new("UIStroke", Main)
MS.Color = Color3.fromRGB(255, 140, 0)
MS.Thickness = 2
MS.Transparency = 0.4

local TB = Instance.new("Frame", Main)
TB.Size = UDim2.new(1, 0, 0, 36)
TB.BackgroundColor3 = Color3.fromRGB(25, 28, 40)
TB.BorderSizePixel = 0
Instance.new("UICorner", TB).CornerRadius = UDim.new(0, 14)

local Title = Instance.new("TextLabel", TB)
Title.Size = UDim2.new(1, -100, 1, 0)
Title.Position = UDim2.new(0, 42, 0, 0)
Title.BackgroundTransparency = 1
Title.Text = "⚡ SCRIPT BY KOMIXS"
Title.TextColor3 = Color3.fromRGB(255, 215, 0)
Title.Font = Enum.Font.GothamBold
Title.TextSize = 14
Title.TextXAlignment = Enum.TextXAlignment.Left

task.spawn(function()
    while true do
        Title.TextColor3 = Color3.fromHSV(tick() * 0.15 % 1, 0.7, 1)
        task.wait(0.05)
    end
end)

local ClsB = Instance.new("TextButton", TB)
ClsB.Size = UDim2.new(0, 26, 0, 26)
ClsB.Position = UDim2.new(1, -32, 0, 5)
ClsB.BackgroundColor3 = Color3.fromRGB(200, 60, 60)
ClsB.Text = "✕"
ClsB.TextColor3 = Color3.fromRGB(255, 255, 255)
ClsB.Font = Enum.Font.GothamBold
ClsB.TextSize = 14
Instance.new("UICorner", ClsB).CornerRadius = UDim.new(0, 8)

local TabBar = Instance.new("Frame", Main)
TabBar.Size = UDim2.new(1, -20, 0, 32)
TabBar.Position = UDim2.new(0, 10, 0, 44)
TabBar.BackgroundColor3 = Color3.fromRGB(22, 24, 32)
TabBar.BorderSizePixel = 0
Instance.new("UICorner", TabBar).CornerRadius = UDim.new(0, 8)

local TScr = Instance.new("ScrollingFrame", TabBar)
TScr.Size = UDim2.new(1, 0, 1, 0)
TScr.BackgroundTransparency = 1
TScr.BorderSizePixel = 0
TScr.ScrollBarThickness = 0
TScr.AutomaticCanvasSize = Enum.AutomaticSize.X
TScr.ScrollingDirection = Enum.ScrollingDirection.X
local TLay = Instance.new("UIListLayout", TScr)
TLay.FillDirection = Enum.FillDirection.Horizontal
TLay.Padding = UDim.new(0, 4)
local TPad = Instance.new("UIPadding", TScr)
TPad.PaddingLeft = UDim.new(0, 5)
TPad.PaddingTop = UDim.new(0, 3)

local Content = Instance.new("Frame", Main)
Content.Size = UDim2.new(1, -20, 1, -100)
Content.Position = UDim2.new(0, 10, 0, 82)
Content.BackgroundTransparency = 1

local pages = {}
local function createTab(name)
    local btn = Instance.new("TextButton", TScr)
    btn.Size = UDim2.new(0, 80, 0, 26)
    btn.BackgroundColor3 = Color3.fromRGB(38, 42, 58)
    btn.Text = name
    btn.TextColor3 = Color3.fromRGB(230, 230, 240)
    btn.Font = Enum.Font.GothamBold
    btn.TextSize = 11
    btn.AutoButtonColor = false
    Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 6)
    local page = Instance.new("ScrollingFrame", Content)
    page.Size = UDim2.new(1, 0, 1, 0)
    page.BackgroundTransparency = 1
    page.BorderSizePixel = 0
    page.ScrollBarThickness = 4
    page.ScrollBarImageColor3 = Color3.fromRGB(255, 140, 0)
    page.AutomaticCanvasSize = Enum.AutomaticSize.Y
    page.Visible = false
    Instance.new("UIListLayout", page).Padding = UDim.new(0, 6)
    pages[name] = {btn = btn, page = page}
    btn.MouseButton1Click:Connect(function()
        for _, p in pairs(pages) do
            p.page.Visible = false
            TS:Create(p.btn, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(38, 42, 58)}):Play()
        end
        page.Visible = true
        TS:Create(btn, TweenInfo.new(0.2), {BackgroundColor3 = Color3.fromRGB(255, 140, 0)}):Play()
    end)
    return page
end

local toggles = {}
local function makeToggle(parent, name, y, cb)
    local btn = Instance.new("TextButton", parent)
    btn.Size = UDim2.new(1, -10, 0, 30)
    btn.Position = UDim2.new(0, 5, 0, y)
    btn.BackgroundColor3 = Color3.fromRGB(38, 42, 58)
    btn.Text = "  " .. name .. "  [ OFF ]"
    btn.TextColor3 = Color3.fromRGB(230, 230, 240)
    btn.Font = Enum.Font.Gotham
    btn.TextSize = 12
    btn.TextXAlignment = Enum.TextXAlignment.Left
    btn.AutoButtonColor = false
    Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 6)
    local state = false
    btn.MouseButton1Click:Connect(function()
        state = not state
        if state then
            btn.Text = "  " .. name .. "  [ ON ]"
            TS:Create(btn, TweenInfo.new(0.3, Enum.EasingStyle.Back), {BackgroundColor3 = Color3.fromRGB(60, 200, 100)}):Play()
        else
            btn.Text = "  " .. name .. "  [ OFF ]"
            TS:Create(btn, TweenInfo.new(0.3), {BackgroundColor3 = Color3.fromRGB(38, 42, 58)}):Play()
        end
        cb(state)
    end)
    toggles[name] = {btn = btn, state = false}
    return btn
end

TS:Create(Main, TweenInfo.new(0.5, Enum.EasingStyle.Quart), {Position = UDim2.new(0, 40, 0.5, -190)}):Play()

ClsB.MouseButton1Click:Connect(function()
    TS:Create(Main, TweenInfo.new(0.4, Enum.EasingStyle.Quart), {Position = UDim2.new(0, -600, 0.5, -190)}):Play()
    task.wait(0.4)
    Main.Visible = false
end)

local GrabPage = createTab("Grab")
local AuraPage = createTab("Aura")
local ProtectPage = createTab("Protect")
local CombatPage = createTab("Combat")

local function getTarget()
    local gp = Workspace:FindFirstChild("GrabParts")
    if not gp then return nil end
    local g = gp:FindFirstChild("GrabPart")
    if not g then return nil end
    local w = g:FindFirstChild("WeldConstraint")
    if not w or not w.Part1 then return nil end
    return w.Part1
end

local flingOn, superFlingOn, killOn, ragdollOn, freezeOn, spinOn, killAllOn, flingAllOn
makeToggle(GrabPage, "🌀 Fling Grab", 0, function(s) flingOn = s end)
makeToggle(GrabPage, "🚀 Super Fling", 40, function(s) superFlingOn = s end)
makeToggle(GrabPage, "💀 Kill Grab", 80, function(s) killOn = s end)
makeToggle(GrabPage, "🦴 Ragdoll Grab", 120, function(s) ragdollOn = s end)
makeToggle(GrabPage, "🧊 Freeze Grab", 160, function(s) freezeOn = s end)
makeToggle(GrabPage, "🎡 Spin Grab", 200, function(s) spinOn = s end)
makeToggle(GrabPage, "☠️ Kill All", 240, function(s) killAllOn = s end)
makeToggle(GrabPage, "🌪️ Fling All", 280, function(s) flingAllOn = s end)

task.spawn(function()
    while true do
        pcall(function()
            local t = getTarget()
            if t and t.Parent then
                if flingOn then t.Velocity = Vector3.new(0, 800, 0) end
                if superFlingOn then t.Velocity = Vector3.new(0, 9999, 0) end
                if killOn then
                    local h = t.Parent:FindFirstChildOfClass("Humanoid")
                    if h then h.Health = 0 end
                end
                if ragdollOn then
                    local h = t.Parent:FindFirstChildOfClass("Humanoid")
                    if h then h:ChangeState(Enum.HumanoidStateType.Ragdoll); h.PlatformStand = true end
                end
                if freezeOn then t.Anchored = true end
                if spinOn then
                    local b = t:FindFirstChild("SpinBAV") or Instance.new("BodyAngularVelocity", t)
                    b.Name = "SpinBAV"
                    b.AngularVelocity = Vector3.new(0, 50, 0)
                    b.MaxTorque = Vector3.new(9e9, 9e9, 9e9)
                end
            end
            if killAllOn then
                for _, p in ipairs(Players:GetPlayers()) do
                    if p ~= LP and p.Character then
                        local h = p.Character:FindFirstChildOfClass("Humanoid")
                        if h then h.Health = 0 end
                    end
                end
            end
            if flingAllOn then
                for _, p in ipairs(Players:GetPlayers()) do
                    if p ~= LP and p.Character then
                        local hrp = p.Character:FindFirstChild("HumanoidRootPart")
                        if hrp then hrp.Velocity = Vector3.new(math.random(-500,500), 800, math.random(-500,500)) end
                    end
                end
            end
        end)
        task.wait(0.1)
    end
end)

local auraRadius = 30
local flingAura, killAura, freezeAura, ragdollAura
makeToggle(AuraPage, "🌀 Fling Aura", 0, function(s) flingAura = s end)
makeToggle(AuraPage, "💀 Kill Aura", 40, function(s) killAura = s end)
makeToggle(AuraPage, "🧊 Freeze Aura", 80, function(s) freezeAura = s end)
makeToggle(AuraPage, "🦴 Ragdoll Aura", 120, function(s) ragdollAura = s end)

task.spawn(function()
    while true do
        pcall(function()
            local myHrp = LP.Character and LP.Character:FindFirstChild("HumanoidRootPart")
            if not myHrp then return end
            for _, p in ipairs(Players:GetPlayers()) do
                if p ~= LP and p.Character then
                    local hrp = p.Character:FindFirstChild("HumanoidRootPart")
                    local hum = p.Character:FindFirstChildOfClass("Humanoid")
                    if hrp and hum then
                        local d = (hrp.Position - myHrp.Position).Magnitude
                        if d <= auraRadius then
                            if flingAura then hrp.Velocity = Vector3.new(0, 500, 0) end
                            if killAura then hum.Health = 0 end
                            if freezeAura then hrp.Anchored = true end
                            if ragdollAura then hum:ChangeState(Enum.HumanoidStateType.Ragdoll); hum.PlatformStand = true end
                        end
                    end
                end
            end
        end)
        task.wait(0.1)
    end
end)

local antiFlingOn, antiGrabSoft, godmode
makeToggle(ProtectPage, "🛡️ Anti-Fling", 0, function(s) antiFlingOn = s end)
makeToggle(ProtectPage, "🚫 Anti-Grab (Soft)", 40, function(s) antiGrabSoft = s end)
makeToggle(ProtectPage, "👼 Godmode", 80, function(s) godmode = s end)

task.spawn(function()
    while true do
        pcall(function()
            local char = LP.Character
            if not char then return end
            local hrp = char:FindFirstChild("HumanoidRootPart")
            local hum = char:FindFirstChildOfClass("Humanoid")
            if not hrp or not hum then return end
            if antiFlingOn then
                if hrp.Velocity.Magnitude > 100 then hrp.Velocity = Vector3.zero end
                hrp.RotVelocity = Vector3.zero
            end
            if antiGrabSoft then
                local gp = Workspace:FindFirstChild("GrabParts")
                if gp then
                    hrp.Anchored = false
                    hum.PlatformStand = false
                end
            end
            if godmode then
                hum.MaxHealth = math.huge
                hum.Health = math.huge
            end
        end)
        task.wait(0.1)
    end
end)

local killAllI, ragdollAllOn
makeToggle(CombatPage, "☠️ Kill All", 0, function(s) killAllI = s end)
makeToggle(CombatPage, "🦴 Ragdoll All", 40, function(s) ragdollAllOn = s end)

task.spawn(function()
    while true do
        pcall(function()
            for _, p in ipairs(Players:GetPlayers()) do
                if p ~= LP and p.Character then
                    local h = p.Character:FindFirstChildOfClass("Humanoid")
                    if h then
                        if killAllI then h.Health = 0 end
                        if ragdollAllOn then h:ChangeState(Enum.HumanoidStateType.Ragdoll); h.PlatformStand = true end
                    end
                end
            end
        end)
        task.wait(0.5)
    end
end)

print("========================================")
print("  SCRIPT BY KOMIXS v4.0")
print("  Загружено ✓")
print("========================================")
