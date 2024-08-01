# LOL



local Checkpoints = workspace.Checkpoints

game.Players.PlayerAdded:Connect(function(plr)
	
	local leaderstats = Instance.new("Folder", plr)
	
	leaderstats.Name = "leaderstats"
	local Checkpoint = Instance.new("IntValue", leaderstats)
	
	Checkpoint.Name = "Stage"
	Checkpoint.Value = 1
	
	plr.CharacterAdded:Connect(function(char)
		wait()
		
		if Checkpoint.Value > 1 then
			char:MoveTo(Checkpoints:FindFirstChild(Checkpoint.Value - 1).Position)
		end
		
	end)
	
	
end)

for i, v in pairs(Checkpoints:GetChildren()) do
	
	v.Touched:Connect(function(hit)
		
		if hit.Parent:FindFirstChild("Humanoid") then
			
			local char = hit.Parent
			local plr = game.Players:GetPlayerFromCharacter(char)
			local Checkpoint = plr.leaderstats.Stage
			
			if tonumber(v.Name) == Checkpoint.Value then
				Checkpoint.Value += 1
			end
			
		end
		
	end)
	
end
