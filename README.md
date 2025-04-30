# Scrip-- ESP básico para jogadores (fins de teste educativos)
for _, player in pairs(game.Players:GetPlayers()) do
    if player ~= game.Players.LocalPlayer then
        local espBox = Drawing.new("Text")
        espBox.Text = player.Name
        espBox.Size = 14
        espBox.Center = true
        espBox.Outline = true
        espBox.Color = Color3.fromRGB(255, 0, 0)
        espBox.Visible = true

        game:GetService("RunService").RenderStepped:Connect(function()
            if player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
                local pos, onScreen = workspace.CurrentCamera:WorldToViewportPoint(player.Character.HumanoidRootPart.Position)
                espBox.Position = Vector2.new(pos.X, pos.Y)
                espBox.Visible = onScreen
            else
                espBox.Visible = false
            end
        end)
    end
endt-
