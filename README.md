--[[
  Onix Hub - O Mais Avançado Script para Blox Fruits
  Features: AutoFarm, AutoBoss, AutoQuest, Raids, ESP, Coleta Automática, Upgrade de Raça e Muito Mais!
  Versão: 7.0 (100% Original - Sem Dependências Externas)
]]

-- Serviços
local Players = game:GetService("Players")
local Workspace = game:GetService("Workspace")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local VirtualInputManager = game:GetService("VirtualInputManager")
local Lighting = game:GetService("Lighting")

-- Configurações
local Config = {
    AutoFarm = true,
    AutoQuest = true,
    AutoBoss = true,
    AutoRaid = true,
    AutoThirdSea = true,
    AutoNewWorld = true,
    AutoCollectItems = true,
    AutoCollectFruits = true,
    AutoStoreFruits = true,
    AutoBuyItems = true,
    AutoSoulGuitar = true,
    AutoFarmBone = true,
    AutoFarmEctoplasm = true,
    AutoFarmCandy = true,
    AutoItemQuests = true,
    AutoUpgradeRace = true,
    ESPEnabled = true,
    AntiAFK = true,
    HideUsername = true,
    HideCharacter = true
}

-- Player
local Player = Players.LocalPlayer
local Character = Player.Character or Player.CharacterAdded:Wait()
local HumanoidRootPart = Character:WaitForChild("HumanoidRootPart")
local Humanoid = Character:WaitForChild("Humanoid")

-- Otimização
Lighting.GlobalShadows = false
Lighting.FogEnd = 1e6
settings().Rendering.QualityLevel = 1

-- Modo Stealth
if Config.HideCharacter then
    for _, part in ipairs(Character:GetDescendants()) do
        if part:IsA("BasePart") then
            part.Transparency = 1
        end
    end
end

if Config.HideUsername then
    Player.Name = "[ONIX HUB]"
end

-- Função de Teleporte
local function Teleport(CFramePos)
    pcall(function()
        HumanoidRootPart.C
