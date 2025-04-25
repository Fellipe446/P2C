-- Configurações iniciais
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

-- Função de coleta de peças de arma
local function autoColetarPecasDeArma()
    for _, part in pairs(workspace:GetDescendants()) do
        if part.Name == "PecaDeArma" and part:IsA("BasePart") then
            part.CFrame = character.HumanoidRootPart.CFrame
        end
    end
end

-- Função de coleta de plantas sujas
local function autoColetarPlantasSujas()
    for _, plant in pairs(workspace:GetDescendants()) do
        if plant.Name == "PlantaSuja" and plant:IsA("BasePart") then
            plant.CFrame = character.HumanoidRootPart.CFrame
        end
    end
end

-- Função de limpar plantas sujas
local function autoLimparPlantasSujas()
    for _, plant in pairs(workspace:GetDescendants()) do
        if plant.Name == "PlantaSujaLimpar" and plant:IsA("BasePart") then
            plant.CFrame = character.HumanoidRootPart.CFrame
        end
    end
end

-- Função para ativar Fly
local function ativarFly()
    local bodyVelocity = Instance.new("BodyVelocity")
    bodyVelocity.MaxForce = Vector3.new(10000, 10000, 10000)
    bodyVelocity.Velocity = Vector3.new(0, 50, 0)
    bodyVelocity.Parent = character.HumanoidRootPart
    wait(5) -- Duração do voo
    bodyVelocity:Destroy()
end

-- Função de trabalho automático (Entregador de gás)
local function autoTrabalhoEntregadorDeGas()
    for _, gas in pairs(workspace:GetDescendants()) do
        if gas.Name == "GasParaEntrega" and gas:IsA("BasePart") then
            gas.CFrame = character.HumanoidRootPart.CFrame
            wait(2) -- Simula o tempo de entrega
        end
    end
end

-- Laço principal para ativar as funções continuamente
while wait(1) do
    autoColetarPecasDeArma()
    autoColetarPlantasSujas()
    autoLimparPlantasSujas()
    autoTrabalhoEntregadorDeGas()
end

-- Fly pode ser ativado manualmente usando um comando
ativarFly()
