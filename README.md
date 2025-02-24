
local player = game.Players.LocalPlayer
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = player:WaitForChild("PlayerGui")


function createButton(text, position, callback)
    local button = Instance.new("TextButton")
    button.Parent = screenGui
    button.Size = UDim2.new(0, 200, 0, 50)
    button.Position = position
    button.Text = text
    button.BackgroundColor3 = Color3.fromRGB(0, 255, 0)  -- Cor do botão
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
    button.Font = Enum.Font.SourceSans
    button.TextSize = 24

    
    button.MouseButton1Click:Connect(callback)
end


local autoFarmActive = false
local attackEnemiesActive = false
local collectFruitsActive = false


function toggleAutoFarm()
    autoFarmActive = not autoFarmActive
    if autoFarmActive then
        print("Auto-Farm Ativado!")
        
    else
        print("Auto-Farm Desativado!")
        
    end
end


function toggleAttackEnemies()
    attackEnemiesActive = not attackEnemiesActive
    if attackEnemiesActive then
        print("Atacar Inimigos Ativado!")
        
    else
        print("Atacar Inimigos Desativado!")
        
    end
end


function toggleCollectFruits()
    collectFruitsActive = not collectFruitsActive
    if collectFruitsActive then
        print("Coletar Frutas Ativado!")
        
    else
        print("Coletar Frutas Desativado!")
        
    end
end


function startAutoFarm()
    while autoFarmActive do
        if attackEnemiesActive then
            attackEnemies()  
        end
        if collectFruitsActive then
            collectFruits()  
        end
        wait(5)  
    end
end


createButton("Ativar/Desativar Auto-Farm", UDim2.new(0.5, -100, 0.2, 0), toggleAutoFarm)
createButton("Ativar/Desativar Atacar Inimigos", UDim2.new(0.5, -100, 0.3, 0), toggleAttackEnemies)
createButton("Ativar/Desativar Coletar Frutas", UDim2.new(0.5, -100, 0.4, 0), toggleCollectFruits)


game:GetService("RunService").Heartbeat:Connect(function()
    if autoFarmActive then
        startAutoFarm()
    end
end)
