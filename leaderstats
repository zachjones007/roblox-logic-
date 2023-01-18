local player = game.Players.LocalPlayer
local foodValue = script:WaitForChild("FoodValue")

local leaderstats = Instance.new("Folder")
leaderstats.Name = "leaderstats"
leaderstats.Parent = player

local Level = Instance.new("IntValue")
Level.Name = "Level"
Level.Parent = leaderstats
Level.Value = 1

local Food = Instance.new("IntValue")
Food.Name = "Food"
Food.Parent = leaderstats
Food.Value = 0

local foodObjects = {}
local model = script.Parent -- Assign the model to the variable "model"

local function spawnFood()
	for i = 1, 15 do
		local food = foodValue:Clone()
		food.Parent = model -- set the parent of the food object to the model
		food.CFrame = model.PrimaryPart.CFrame + Vector3.new(math.random(-10, 10), 0, math.random(-10, 10))
		foodObjects[i] = food
		food.Touched:Connect(function(hit)
			if hit.Parent == player.Character then
				local inventory = player:WaitForChild("inventory")
				if not inventory then
					inventory = Instance.new("Folder")
					inventory.Name = "inventory"
					inventory.Parent = player
				end
				local foodItem = foodValue:Clone()
				foodItem.Parent = inventory
				food:Destroy()
				Food.Value = Food.Value + foodItem.Value
				if Food.Value >= 25 then
					Food.Value = Food.Value - 25
					Level.Value = Level.Value + 1
					print("Leveled up!")
				end
			end
		end)
	end
end

local function despawnFood()
	for i = 1, #foodObjects do
		foodObjects[i]:Destroy()
	end
end

spawnFood()


while true do
	wait(30)
	despawnFood()
	spawnFood()
end
