local animal = script.Parent --Assuming that the script is located in the animal object
local food = script:WaitForChild("Food") --Assuming that the food value is a child of the script

if success and animal.Health > 0 then
    local Level = animal:FindFirstChild("Level")
    if Level then
        if food.Value >= 25 then
            food.Value = food.Value - 25
            Level.Value = Level.Value + 1
            animal.Size = animal.Size * 2 -- Double the size of the animal
            print("Animal Leveled up!")
        end
    end
end
