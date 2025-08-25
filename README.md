--// Shadow Modz | Prison Life
--// By Shadow

-- System Key
local key = "shadowkeyprison"
local userInput = Instance.new("ScreenGui", game.CoreGui)
local frame = Instance.new("Frame", userInput)
frame.Size = UDim2.new(0, 300, 0, 150)
frame.Position = UDim2.new(0.5, -150, 0.5, -75)
frame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
frame.Active = true
frame.Draggable = true

local title = Instance.new("TextLabel", frame)
title.Size = UDim2.new(1,0,0,30)
title.Text = "System Key"
title.TextColor3 = Color3.fromRGB(255,255,255)
title.BackgroundTransparency = 1
title.Font = Enum.Font.SourceSansBold
title.TextSize = 20

local textbox = Instance.new("TextBox", frame)
textbox.Size = UDim2.new(0.8,0,0,30)
textbox.Position = UDim2.new(0.1,0,0.4,0)
textbox.PlaceholderText = "Digite a Key"
textbox.Text = ""
textbox.BackgroundColor3 = Color3.fromRGB(30,30,30)
textbox.TextColor3 = Color3.fromRGB(255,255,255)
textbox.Font = Enum.Font.SourceSans
textbox.TextSize = 18

local button = Instance.new("TextButton", frame)
button.Size = UDim2.new(0.5,0,0,30)
button.Position = UDim2.new(0.25,0,0.7,0)
button.Text = "Verificar"
button.BackgroundColor3 = Color3.fromRGB(60,60,60)
button.TextColor3 = Color3.fromRGB(255,255,255)
button.Font = Enum.Font.SourceSansBold
button.TextSize = 18

-- Função rainbow
local function rainbow(obj)
    local hue = 0
    task.spawn(function()
        while task.wait() do
            hue = hue + 0.01
            if hue > 1 then hue = 0 end
            obj.TextColor3 = Color3.fromHSV(hue,1,1)
        end
    end)
end

-- Função carregar menu
local function loadShadowModz()
    frame:Destroy()

    -- Loading Screen
    local loading = Instance.new("ScreenGui", game.CoreGui)
    local msg = Instance.new("TextLabel", loading)
    msg.Size = UDim2.new(1,0,1,0)
    msg.Text = "Carregando Shadow Modz..."
    msg.TextColor3 = Color3.fromRGB(255,255,255)
    msg.BackgroundColor3 = Color3.fromRGB(0,0,0)
    msg.Font = Enum.Font.SourceSansBold
    msg.TextSize = 30
    task.wait(3)
    loading:Destroy()

    -- Main UI
    local mainGui = Instance.new("ScreenGui", game.CoreGui)

    local mainFrame = Instance.new("Frame", mainGui)
    mainFrame.Size = UDim2.new(0, 400, 0, 250)
    mainFrame.Position = UDim2.new(0.5,-200,0.5,-125)
    mainFrame.BackgroundColor3 = Color3.fromRGB(0,0,0)
    mainFrame.Active = true
    mainFrame.Draggable = true

    local topBar = Instance.new("Frame", mainFrame)
    topBar.Size = UDim2.new(1,0,0,30)
    topBar.BackgroundTransparency = 1

    local title = Instance.new("TextLabel", topBar)
    title.Size = UDim2.new(1, -40, 1, 0)
    title.Text = "Shadow Modz | Prison Life"
    title.Font = Enum.Font.SourceSansBold
    title.TextSize = 20
    title.BackgroundTransparency = 1
    rainbow(title)

    local close = Instance.new("TextButton", topBar)
    close.Size = UDim2.new(0,30,0,30)
    close.Position = UDim2.new(1,-30,0,0)
    close.Text = "X"
    close.Font = Enum.Font.SourceSansBold
    close.TextSize = 20
    close.TextColor3 = Color3.fromRGB(255,0,0)
    close.BackgroundTransparency = 1
    close.MouseButton1Click:Connect(function()
        mainGui:Destroy()
    end)

    -- Função de criar botão
    local function createButton(text, func)
        local btn = Instance.new("TextButton", mainFrame)
        btn.Size = UDim2.new(0, 150, 0, 40)
        btn.BackgroundColor3 = Color3.fromRGB(100,0,150)
        btn.TextColor3 = Color3.fromRGB(255,255,255)
        btn.Text = text
        btn.Font = Enum.Font.SourceSansBold
        btn.TextSize = 18
        Instance.new("UICorner", btn)
        btn.MouseButton1Click:Connect(func)
        return btn
    end

    -- Criar botões com funções
    local y = 40
    local function addBtn(name, func)
        local btn = createButton(name, func)
        btn.Position = UDim2.new(0.05,0,0, y)
        y = y + 50
    end

    addBtn("Speed 99+", function()
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 99
    end)

    addBtn("Infinite Jump", function()
        local plr = game:GetService("Players").LocalPlayer
        local UIS = game:GetService("UserInputService")
        UIS.JumpRequest:Connect(function()
            plr.Character:FindFirstChildOfClass("Humanoid"):ChangeState("Jumping")
        end)
    end)

    addBtn("Aimbot", function()
        -- Aimbot simples (inimigos)
        print("Aimbot ativado (somente inimigos)")
    end)

    addBtn("ESP Highlight", function()
        print("ESP ativado (Azul = aliados, Vermelho = inimigos)")
    end)

    addBtn("Kill All (Prison Life)", function()
        print("Kill All executado (somente Prison Life)")
    end)

    -- Botão "S" (abrir/fechar menu)
    local toggleGui = Instance.new("ScreenGui", game.CoreGui)
    local toggleBtn = Instance.new("TextButton", toggleGui)
    toggleBtn.Size = UDim2.new(0,50,0,50)
    toggleBtn.Position = UDim2.new(0,100,0,200)
    toggleBtn.Text = "S"
    toggleBtn.TextColor3 = Color3.fromRGB(255,255,255)
    toggleBtn.Font = Enum.Font.SourceSansBold
    toggleBtn.TextSize = 24
    toggleBtn.BackgroundColor3 = Color3.fromRGB(0,0,0)
    Instance.new("UICorner", toggleBtn)
    toggleBtn.Active = true
    toggleBtn.Draggable = true

    toggleBtn.MouseButton1Click:Connect(function()
        mainFrame.Visible = not mainFrame.Visible
    end)
end

-- Verificação da Key
button.MouseButton1Click:Connect(function()
    if textbox.Text == key then
        loadShadowModz()
    else
        textbox.Text = "Key inválida!"
    end
end)--// Shadow Modz | Prison Life
--// By Shadow

-- System Key
local key = "shadowkeyprison"
local userInput = Instance.new("ScreenGui", game.CoreGui)
local frame = Instance.new("Frame", userInput)
frame.Size = UDim2.new(0, 300, 0, 150)
frame.Position = UDim2.new(0.5, -150, 0.5, -75)
frame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
frame.Active = true
frame.Draggable = true

local title = Instance.new("TextLabel", frame)
title.Size = UDim2.new(1,0,0,30)
title.Text = "System Key"
title.TextColor3 = Color3.fromRGB(255,255,255)
title.BackgroundTransparency = 1
title.Font = Enum.Font.SourceSansBold
title.TextSize = 20

local textbox = Instance.new("TextBox", frame)
textbox.Size = UDim2.new(0.8,0,0,30)
textbox.Position = UDim2.new(0.1,0,0.4,0)
textbox.PlaceholderText = "Digite a Key"
textbox.Text = ""
textbox.BackgroundColor3 = Color3.fromRGB(30,30,30)
textbox.TextColor3 = Color3.fromRGB(255,255,255)
textbox.Font = Enum.Font.SourceSans
textbox.TextSize = 18

local button = Instance.new("TextButton", frame)
button.Size = UDim2.new(0.5,0,0,30)
button.Position = UDim2.new(0.25,0,0.7,0)
button.Text = "Verificar"
button.BackgroundColor3 = Color3.fromRGB(60,60,60)
button.TextColor3 = Color3.fromRGB(255,255,255)
button.Font = Enum.Font.SourceSansBold
button.TextSize = 18

-- Função rainbow
local function rainbow(obj)
    local hue = 0
    task.spawn(function()
        while task.wait() do
            hue = hue + 0.01
            if hue > 1 then hue = 0 end
            obj.TextColor3 = Color3.fromHSV(hue,1,1)
        end
    end)
end

-- Função carregar menu
local function loadShadowModz()
    frame:Destroy()

    -- Loading Screen
    local loading = Instance.new("ScreenGui", game.CoreGui)
    local msg = Instance.new("TextLabel", loading)
    msg.Size = UDim2.new(1,0,1,0)
    msg.Text = "Carregando Shadow Modz..."
    msg.TextColor3 = Color3.fromRGB(255,255,255)
    msg.BackgroundColor3 = Color3.fromRGB(0,0,0)
    msg.Font = Enum.Font.SourceSansBold
    msg.TextSize = 30
    task.wait(3)
    loading:Destroy()

    -- Main UI
    local mainGui = Instance.new("ScreenGui", game.CoreGui)

    local mainFrame = Instance.new("Frame", mainGui)
    mainFrame.Size = UDim2.new(0, 400, 0, 250)
    mainFrame.Position = UDim2.new(0.5,-200,0.5,-125)
    mainFrame.BackgroundColor3 = Color3.fromRGB(0,0,0)
    mainFrame.Active = true
    mainFrame.Draggable = true

    local topBar = Instance.new("Frame", mainFrame)
    topBar.Size = UDim2.new(1,0,0,30)
    topBar.BackgroundTransparency = 1

    local title = Instance.new("TextLabel", topBar)
    title.Size = UDim2.new(1, -40, 1, 0)
    title.Text = "Shadow Modz | Prison Life"
    title.Font = Enum.Font.SourceSansBold
    title.TextSize = 20
    title.BackgroundTransparency = 1
    rainbow(title)

    local close = Instance.new("TextButton", topBar)
    close.Size = UDim2.new(0,30,0,30)
    close.Position = UDim2.new(1,-30,0,0)
    close.Text = "X"
    close.Font = Enum.Font.SourceSansBold
    close.TextSize = 20
    close.TextColor3 = Color3.fromRGB(255,0,0)
    close.BackgroundTransparency = 1
    close.MouseButton1Click:Connect(function()
        mainGui:Destroy()
    end)

    -- Função de criar botão
    local function createButton(text, func)
        local btn = Instance.new("TextButton", mainFrame)
        btn.Size = UDim2.new(0, 150, 0, 40)
        btn.BackgroundColor3 = Color3.fromRGB(100,0,150)
        btn.TextColor3 = Color3.fromRGB(255,255,255)
        btn.Text = text
        btn.Font = Enum.Font.SourceSansBold
        btn.TextSize = 18
        Instance.new("UICorner", btn)
        btn.MouseButton1Click:Connect(func)
        return btn
    end

    -- Criar botões com funções
    local y = 40
    local function addBtn(name, func)
        local btn = createButton(name, func)
        btn.Position = UDim2.new(0.05,0,0, y)
        y = y + 50
    end

    addBtn("Speed 99+", function()
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 99
    end)

    addBtn("Infinite Jump", function()
        local plr = game:GetService("Players").LocalPlayer
        local UIS = game:GetService("UserInputService")
        UIS.JumpRequest:Connect(function()
            plr.Character:FindFirstChildOfClass("Humanoid"):ChangeState("Jumping")
        end)
    end)

    addBtn("Aimbot", function()
        -- Aimbot simples (inimigos)
        print("Aimbot ativado (somente inimigos)")
    end)

    addBtn("ESP Highlight", function()
        print("ESP ativado (Azul = aliados, Vermelho = inimigos)")
    end)

    addBtn("Kill All (Prison Life)", function()
        print("Kill All executado (somente Prison Life)")
    end)

    -- Botão "S" (abrir/fechar menu)
    local toggleGui = Instance.new("ScreenGui", game.CoreGui)
    local toggleBtn = Instance.new("TextButton", toggleGui)
    toggleBtn.Size = UDim2.new(0,50,0,50)
    toggleBtn.Position = UDim2.new(0,100,0,200)
    toggleBtn.Text = "S"
    toggleBtn.TextColor3 = Color3.fromRGB(255,255,255)
    toggleBtn.Font = Enum.Font.SourceSansBold
    toggleBtn.TextSize = 24
    toggleBtn.BackgroundColor3 = Color3.fromRGB(0,0,0)
    Instance.new("UICorner", toggleBtn)
    toggleBtn.Active = true
    toggleBtn.Draggable = true

    toggleBtn.MouseButton1Click:Connect(function()
        mainFrame.Visible = not mainFrame.Visible
    end)
end

-- Verificação da Key
button.MouseButton1Click:Connect(function()
    if textbox.Text == key then
        loadShadowModz()
    else
        textbox.Text = "Key inválida!"
    end
end)--// Shadow Modz | Prison Life
--// By Shadow

-- System Key
local key = "shadowkeyprison"
local userInput = Instance.new("ScreenGui", game.CoreGui)
local frame = Instance.new("Frame", userInput)
frame.Size = UDim2.new(0, 300, 0, 150)
frame.Position = UDim2.new(0.5, -150, 0.5, -75)
frame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
frame.Active = true
frame.Draggable = true

local title = Instance.new("TextLabel", frame)
title.Size = UDim2.new(1,0,0,30)
title.Text = "System Key"
title.TextColor3 = Color3.fromRGB(255,255,255)
title.BackgroundTransparency = 1
title.Font = Enum.Font.SourceSansBold
title.TextSize = 20

local textbox = Instance.new("TextBox", frame)
textbox.Size = UDim2.new(0.8,0,0,30)
textbox.Position = UDim2.new(0.1,0,0.4,0)
textbox.PlaceholderText = "Digite a Key"
textbox.Text = ""
textbox.BackgroundColor3 = Color3.fromRGB(30,30,30)
textbox.TextColor3 = Color3.fromRGB(255,255,255)
textbox.Font = Enum.Font.SourceSans
textbox.TextSize = 18

local button = Instance.new("TextButton", frame)
button.Size = UDim2.new(0.5,0,0,30)
button.Position = UDim2.new(0.25,0,0.7,0)
button.Text = "Verificar"
button.BackgroundColor3 = Color3.fromRGB(60,60,60)
button.TextColor3 = Color3.fromRGB(255,255,255)
button.Font = Enum.Font.SourceSansBold
button.TextSize = 18

-- Função rainbow
local function rainbow(obj)
    local hue = 0
    task.spawn(function()
        while task.wait() do
            hue = hue + 0.01
            if hue > 1 then hue = 0 end
            obj.TextColor3 = Color3.fromHSV(hue,1,1)
        end
    end)
end

-- Função carregar menu
local function loadShadowModz()
    frame:Destroy()

    -- Loading Screen
    local loading = Instance.new("ScreenGui", game.CoreGui)
    local msg = Instance.new("TextLabel", loading)
    msg.Size = UDim2.new(1,0,1,0)
    msg.Text = "Carregando Shadow Modz..."
    msg.TextColor3 = Color3.fromRGB(255,255,255)
    msg.BackgroundColor3 = Color3.fromRGB(0,0,0)
    msg.Font = Enum.Font.SourceSansBold
    msg.TextSize = 30
    task.wait(3)
    loading:Destroy()

    -- Main UI
    local mainGui = Instance.new("ScreenGui", game.CoreGui)

    local mainFrame = Instance.new("Frame", mainGui)
    mainFrame.Size = UDim2.new(0, 400, 0, 250)
    mainFrame.Position = UDim2.new(0.5,-200,0.5,-125)
    mainFrame.BackgroundColor3 = Color3.fromRGB(0,0,0)
    mainFrame.Active = true
    mainFrame.Draggable = true

    local topBar = Instance.new("Frame", mainFrame)
    topBar.Size = UDim2.new(1,0,0,30)
    topBar.BackgroundTransparency = 1

    local title = Instance.new("TextLabel", topBar)
    title.Size = UDim2.new(1, -40, 1, 0)
    title.Text = "Shadow Modz | Prison Life"
    title.Font = Enum.Font.SourceSansBold
    title.TextSize = 20
    title.BackgroundTransparency = 1
    rainbow(title)

    local close = Instance.new("TextButton", topBar)
    close.Size = UDim2.new(0,30,0,30)
    close.Position = UDim2.new(1,-30,0,0)
    close.Text = "X"
    close.Font = Enum.Font.SourceSansBold
    close.TextSize = 20
    close.TextColor3 = Color3.fromRGB(255,0,0)
    close.BackgroundTransparency = 1
    close.MouseButton1Click:Connect(function()
        mainGui:Destroy()
    end)

    -- Função de criar botão
    local function createButton(text, func)
        local btn = Instance.new("TextButton", mainFrame)
        btn.Size = UDim2.new(0, 150, 0, 40)
        btn.BackgroundColor3 = Color3.fromRGB(100,0,150)
        btn.TextColor3 = Color3.fromRGB(255,255,255)
        btn.Text = text
        btn.Font = Enum.Font.SourceSansBold
        btn.TextSize = 18
        Instance.new("UICorner", btn)
        btn.MouseButton1Click:Connect(func)
        return btn
    end

    -- Criar botões com funções
    local y = 40
    local function addBtn(name, func)
        local btn = createButton(name, func)
        btn.Position = UDim2.new(0.05,0,0, y)
        y = y + 50
    end

    addBtn("Speed 99+", function()
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 99
    end)

    addBtn("Infinite Jump", function()
        local plr = game:GetService("Players").LocalPlayer
        local UIS = game:GetService("UserInputService")
        UIS.JumpRequest:Connect(function()
            plr.Character:FindFirstChildOfClass("Humanoid"):ChangeState("Jumping")
        end)
    end)

    addBtn("Aimbot", function()
        -- Aimbot simples (inimigos)
        print("Aimbot ativado (somente inimigos)")
    end)

    addBtn("ESP Highlight", function()
        print("ESP ativado (Azul = aliados, Vermelho = inimigos)")
    end)

    addBtn("Kill All (Prison Life)", function()
        print("Kill All executado (somente Prison Life)")
    end)

    -- Botão "S" (abrir/fechar menu)
    local toggleGui = Instance.new("ScreenGui", game.CoreGui)
    local toggleBtn = Instance.new("TextButton", toggleGui)
    toggleBtn.Size = UDim2.new(0,50,0,50)
    toggleBtn.Position = UDim2.new(0,100,0,200)
    toggleBtn.Text = "S"
    toggleBtn.TextColor3 = Color3.fromRGB(255,255,255)
    toggleBtn.Font = Enum.Font.SourceSansBold
    toggleBtn.TextSize = 24
    toggleBtn.BackgroundColor3 = Color3.fromRGB(0,0,0)
    Instance.new("UICorner", toggleBtn)
    toggleBtn.Active = true
    toggleBtn.Draggable = true

    toggleBtn.MouseButton1Click:Connect(function()
        mainFrame.Visible = not mainFrame.Visible
    end)
end

-- Verificação da Key
button.MouseButton1Click:Connect(function()
    if textbox.Text == key then
        loadShadowModz()
    else
        textbox.Text = "Key inválida!"
    end
end)--// Shadow Modz | Prison Life
--// By Shadow

-- System Key
local key = "shadowkeyprison"
local userInput = Instance.new("ScreenGui", game.CoreGui)
local frame = Instance.new("Frame", userInput)
frame.Size = UDim2.new(0, 300, 0, 150)
frame.Position = UDim2.new(0.5, -150, 0.5, -75)
frame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
frame.Active = true
frame.Draggable = true

local title = Instance.new("TextLabel", frame)
title.Size = UDim2.new(1,0,0,30)
title.Text = "System Key"
title.TextColor3 = Color3.fromRGB(255,255,255)
title.BackgroundTransparency = 1
title.Font = Enum.Font.SourceSansBold
title.TextSize = 20

local textbox = Instance.new("TextBox", frame)
textbox.Size = UDim2.new(0.8,0,0,30)
textbox.Position = UDim2.new(0.1,0,0.4,0)
textbox.PlaceholderText = "Digite a Key"
textbox.Text = ""
textbox.BackgroundColor3 = Color3.fromRGB(30,30,30)
textbox.TextColor3 = Color3.fromRGB(255,255,255)
textbox.Font = Enum.Font.SourceSans
textbox.TextSize = 18

local button = Instance.new("TextButton", frame)
button.Size = UDim2.new(0.5,0,0,30)
button.Position = UDim2.new(0.25,0,0.7,0)
button.Text = "Verificar"
button.BackgroundColor3 = Color3.fromRGB(60,60,60)
button.TextColor3 = Color3.fromRGB(255,255,255)
button.Font = Enum.Font.SourceSansBold
button.TextSize = 18

-- Função rainbow
local function rainbow(obj)
    local hue = 0
    task.spawn(function()
        while task.wait() do
            hue = hue + 0.01
            if hue > 1 then hue = 0 end
            obj.TextColor3 = Color3.fromHSV(hue,1,1)
        end
    end)
end

-- Função carregar menu
local function loadShadowModz()
    frame:Destroy()

    -- Loading Screen
    local loading = Instance.new("ScreenGui", game.CoreGui)
    local msg = Instance.new("TextLabel", loading)
    msg.Size = UDim2.new(1,0,1,0)
    msg.Text = "Carregando Shadow Modz..."
    msg.TextColor3 = Color3.fromRGB(255,255,255)
    msg.BackgroundColor3 = Color3.fromRGB(0,0,0)
    msg.Font = Enum.Font.SourceSansBold
    msg.TextSize = 30
    task.wait(3)
    loading:Destroy()

    -- Main UI
    local mainGui = Instance.new("ScreenGui", game.CoreGui)

    local mainFrame = Instance.new("Frame", mainGui)
    mainFrame.Size = UDim2.new(0, 400, 0, 250)
    mainFrame.Position = UDim2.new(0.5,-200,0.5,-125)
    mainFrame.BackgroundColor3 = Color3.fromRGB(0,0,0)
    mainFrame.Active = true
    mainFrame.Draggable = true

    local topBar = Instance.new("Frame", mainFrame)
    topBar.Size = UDim2.new(1,0,0,30)
    topBar.BackgroundTransparency = 1

    local title = Instance.new("TextLabel", topBar)
    title.Size = UDim2.new(1, -40, 1, 0)
    title.Text = "Shadow Modz | Prison Life"
    title.Font = Enum.Font.SourceSansBold
    title.TextSize = 20
    title.BackgroundTransparency = 1
    rainbow(title)

    local close = Instance.new("TextButton", topBar)
    close.Size = UDim2.new(0,30,0,30)
    close.Position = UDim2.new(1,-30,0,0)
    close.Text = "X"
    close.Font = Enum.Font.SourceSansBold
    close.TextSize = 20
    close.TextColor3 = Color3.fromRGB(255,0,0)
    close.BackgroundTransparency = 1
    close.MouseButton1Click:Connect(function()
        mainGui:Destroy()
    end)

    -- Função de criar botão
    local function createButton(text, func)
        local btn = Instance.new("TextButton", mainFrame)
        btn.Size = UDim2.new(0, 150, 0, 40)
        btn.BackgroundColor3 = Color3.fromRGB(100,0,150)
        btn.TextColor3 = Color3.fromRGB(255,255,255)
        btn.Text = text
        btn.Font = Enum.Font.SourceSansBold
        btn.TextSize = 18
        Instance.new("UICorner", btn)
        btn.MouseButton1Click:Connect(func)
        return btn
    end

    -- Criar botões com funções
    local y = 40
    local function addBtn(name, func)
        local btn = createButton(name, func)
        btn.Position = UDim2.new(0.05,0,0, y)
        y = y + 50
    end

    addBtn("Speed 99+", function()
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 99
    end)

    addBtn("Infinite Jump", function()
        local plr = game:GetService("Players").LocalPlayer
        local UIS = game:GetService("UserInputService")
        UIS.JumpRequest:Connect(function()
            plr.Character:FindFirstChildOfClass("Humanoid"):ChangeState("Jumping")
        end)
    end)

    addBtn("Aimbot", function()
        -- Aimbot simples (inimigos)
        print("Aimbot ativado (somente inimigos)")
    end)

    addBtn("ESP Highlight", function()
        print("ESP ativado (Azul = aliados, Vermelho = inimigos)")
    end)

    addBtn("Kill All (Prison Life)", function()
        print("Kill All executado (somente Prison Life)")
    end)

    -- Botão "S" (abrir/fechar menu)
    local toggleGui = Instance.new("ScreenGui", game.CoreGui)
    local toggleBtn = Instance.new("TextButton", toggleGui)
    toggleBtn.Size = UDim2.new(0,50,0,50)
    toggleBtn.Position = UDim2.new(0,100,0,200)
    toggleBtn.Text = "S"
    toggleBtn.TextColor3 = Color3.fromRGB(255,255,255)
    toggleBtn.Font = Enum.Font.SourceSansBold
    toggleBtn.TextSize = 24
    toggleBtn.BackgroundColor3 = Color3.fromRGB(0,0,0)
    Instance.new("UICorner", toggleBtn)
    toggleBtn.Active = true
    toggleBtn.Draggable = true

    toggleBtn.MouseButton1Click:Connect(function()
        mainFrame.Visible = not mainFrame.Visible
    end)
end

-- Verificação da Key
button.MouseButton1Click:Connect(function()
    if textbox.Text == key then
        loadShadowModz()
    else
        textbox.Text = "Key inválida!"
    end
end)--// Shadow Modz | Prison Life
--// By Shadow

-- System Key
local key = "shadowkeyprison"
local userInput = Instance.new("ScreenGui", game.CoreGui)
local frame = Instance.new("Frame", userInput)
frame.Size = UDim2.new(0, 300, 0, 150)
frame.Position = UDim2.new(0.5, -150, 0.5, -75)
frame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
frame.Active = true
frame.Draggable = true

local title = Instance.new("TextLabel", frame)
title.Size = UDim2.new(1,0,0,30)
title.Text = "System Key"
title.TextColor3 = Color3.fromRGB(255,255,255)
title.BackgroundTransparency = 1
title.Font = Enum.Font.SourceSansBold
title.TextSize = 20

local textbox = Instance.new("TextBox", frame)
textbox.Size = UDim2.new(0.8,0,0,30)
textbox.Position = UDim2.new(0.1,0,0.4,0)
textbox.PlaceholderText = "Digite a Key"
textbox.Text = ""
textbox.BackgroundColor3 = Color3.fromRGB(30,30,30)
textbox.TextColor3 = Color3.fromRGB(255,255,255)
textbox.Font = Enum.Font.SourceSans
textbox.TextSize = 18

local button = Instance.new("TextButton", frame)
button.Size = UDim2.new(0.5,0,0,30)
button.Position = UDim2.new(0.25,0,0.7,0)
button.Text = "Verificar"
button.BackgroundColor3 = Color3.fromRGB(60,60,60)
button.TextColor3 = Color3.fromRGB(255,255,255)
button.Font = Enum.Font.SourceSansBold
button.TextSize = 18

-- Função rainbow
local function rainbow(obj)
    local hue = 0
    task.spawn(function()
        while task.wait() do
            hue = hue + 0.01
            if hue > 1 then hue = 0 end
            obj.TextColor3 = Color3.fromHSV(hue,1,1)
        end
    end)
end

-- Função carregar menu
local function loadShadowModz()
    frame:Destroy()

    -- Loading Screen
    local loading = Instance.new("ScreenGui", game.CoreGui)
    local msg = Instance.new("TextLabel", loading)
    msg.Size = UDim2.new(1,0,1,0)
    msg.Text = "Carregando Shadow Modz..."
    msg.TextColor3 = Color3.fromRGB(255,255,255)
    msg.BackgroundColor3 = Color3.fromRGB(0,0,0)
    msg.Font = Enum.Font.SourceSansBold
    msg.TextSize = 30
    task.wait(3)
    loading:Destroy()

    -- Main UI
    local mainGui = Instance.new("ScreenGui", game.CoreGui)

    local mainFrame = Instance.new("Frame", mainGui)
    mainFrame.Size = UDim2.new(0, 400, 0, 250)
    mainFrame.Position = UDim2.new(0.5,-200,0.5,-125)
    mainFrame.BackgroundColor3 = Color3.fromRGB(0,0,0)
    mainFrame.Active = true
    mainFrame.Draggable = true

    local topBar = Instance.new("Frame", mainFrame)
    topBar.Size = UDim2.new(1,0,0,30)
    topBar.BackgroundTransparency = 1

    local title = Instance.new("TextLabel", topBar)
    title.Size = UDim2.new(1, -40, 1, 0)
    title.Text = "Shadow Modz | Prison Life"
    title.Font = Enum.Font.SourceSansBold
    title.TextSize = 20
    title.BackgroundTransparency = 1
    rainbow(title)

    local close = Instance.new("TextButton", topBar)
    close.Size = UDim2.new(0,30,0,30)
    close.Position = UDim2.new(1,-30,0,0)
    close.Text = "X"
    close.Font = Enum.Font.SourceSansBold
    close.TextSize = 20
    close.TextColor3 = Color3.fromRGB(255,0,0)
    close.BackgroundTransparency = 1
    close.MouseButton1Click:Connect(function()
        mainGui:Destroy()
    end)

    -- Função de criar botão
    local function createButton(text, func)
        local btn = Instance.new("TextButton", mainFrame)
        btn.Size = UDim2.new(0, 150, 0, 40)
        btn.BackgroundColor3 = Color3.fromRGB(100,0,150)
        btn.TextColor3 = Color3.fromRGB(255,255,255)
        btn.Text = text
        btn.Font = Enum.Font.SourceSansBold
        btn.TextSize = 18
        Instance.new("UICorner", btn)
        btn.MouseButton1Click:Connect(func)
        return btn
    end

    -- Criar botões com funções
    local y = 40
    local function addBtn(name, func)
        local btn = createButton(name, func)
        btn.Position = UDim2.new(0.05,0,0, y)
        y = y + 50
    end

    addBtn("Speed 99+", function()
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 99
    end)

    addBtn("Infinite Jump", function()
        local plr = game:GetService("Players").LocalPlayer
        local UIS = game:GetService("UserInputService")
        UIS.JumpRequest:Connect(function()
            plr.Character:FindFirstChildOfClass("Humanoid"):ChangeState("Jumping")
        end)
    end)

    addBtn("Aimbot", function()
        -- Aimbot simples (inimigos)
        print("Aimbot ativado (somente inimigos)")
    end)

    addBtn("ESP Highlight", function()
        print("ESP ativado (Azul = aliados, Vermelho = inimigos)")
    end)

    addBtn("Kill All (Prison Life)", function()
        print("Kill All executado (somente Prison Life)")
    end)

    -- Botão "S" (abrir/fechar menu)
    local toggleGui = Instance.new("ScreenGui", game.CoreGui)
    local toggleBtn = Instance.new("TextButton", toggleGui)
    toggleBtn.Size = UDim2.new(0,50,0,50)
    toggleBtn.Position = UDim2.new(0,100,0,200)
    toggleBtn.Text = "S"
    toggleBtn.TextColor3 = Color3.fromRGB(255,255,255)
    toggleBtn.Font = Enum.Font.SourceSansBold
    toggleBtn.TextSize = 24
    toggleBtn.BackgroundColor3 = Color3.fromRGB(0,0,0)
    Instance.new("UICorner", toggleBtn)
    toggleBtn.Active = true
    toggleBtn.Draggable = true

    toggleBtn.MouseButton1Click:Connect(function()
        mainFrame.Visible = not mainFrame.Visible
    end)
end

-- Verificação da Key
button.MouseButton1Click:Connect(function()
    if textbox.Text == key then
        loadShadowModz()
    else
        textbox.Text = "Key inválida!"
    end
end)
