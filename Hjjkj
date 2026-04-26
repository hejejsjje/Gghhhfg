-- สร้าง GUI
local player = game.Players.LocalPlayer
local mouse = player:GetMouse()

local screenGui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))

local frame = Instance.new("Frame", screenGui)
frame.Size = UDim2.new(0, 200, 0, 150)
frame.Position = UDim2.new(0.3, 0, 0.3, 0)
frame.BackgroundColor3 = Color3.fromRGB(30,30,30)
frame.Active = true
frame.Draggable = true

-- ปุ่ม Fly
local flyButton = Instance.new("TextButton", frame)
flyButton.Size = UDim2.new(0, 180, 0, 40)
flyButton.Position = UDim2.new(0, 10, 0, 10)
flyButton.Text = "Fly: OFF"
flyButton.BackgroundColor3 = Color3.fromRGB(50,50,50)

-- ปุ่มเพิ่มความเร็ว
local speedButton = Instance.new("TextButton", frame)
speedButton.Size = UDim2.new(0, 180, 0, 40)
speedButton.Position = UDim2.new(0, 10, 0, 60)
speedButton.Text = "Speed x2"
speedButton.BackgroundColor3 = Color3.fromRGB(50,50,50)

-- ตัวแปร
local flying = false
local speed = 16

-- ฟังก์ชัน Fly
local function startFly()
	local character = player.Character or player.CharacterAdded:Wait()
	local hrp = character:WaitForChild("HumanoidRootPart")

	local bodyVelocity = Instance.new("BodyVelocity")
	bodyVelocity.Velocity = Vector3.new(0,0,0)
	bodyVelocity.MaxForce = Vector3.new(1,1,1) * 1e5
	bodyVelocity.Parent = hrp

	while flying do
		bodyVelocity.Velocity = workspace.CurrentCamera.CFrame.LookVector * 50
		wait()
	end

	bodyVelocity:Destroy()
end

-- Toggle Fly
flyButton.MouseButton1Click:Connect(function()
	flying = not flying
	flyButton.Text = "Fly: " .. (flying and "ON" or "OFF")

	if flying then
		startFly()
	end
end)

-- ปรับความเร็ว
speedButton.MouseButton1Click:Connect(function()
	local character = player.Character or player.CharacterAdded:Wait()
	local humanoid = character:WaitForChild("Humanoid")

	speed = speed * 2
	if speed > 100 then
		speed = 16
	end

	humanoid.WalkSpeed = speed
	speedButton.Text = "Speed: " .. speed
end)
