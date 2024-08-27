--[[

    MADE BY vezrr & crtrz ON DISCORD!
    https://discord.gg/DXrGhrxZ9v

]]

local Library = loadstring(game:HttpGet("https://pastebin.com/raw/ry59CnUE"))()
local Window = Library.Create("vezrr & crtrz gui", "yba killer :skull:")
local MainTab = Window:Tab("Main")
local StandTab = Window:Tab("Stand")
local TeleportTab = Window:Tab("Teleports")
local ServerTab = Window:Tab("Server")
local OtherTab = Window:Tab("Other")

--// Player Shit
local Player = game.Players.LocalPlayer
local Character = Player.Character or Player.CharacterAdded:Wait()
Player.CharacterAdded:Connect(function()
    task.wait(1)
    Character = Player.Character
end)
local Humanoid = Character:FindFirstChild("Humanoid") or Character:WaitForChild("Humanoid")
local HumanoidRootPart = Character:FindFirstChild("HumanoidRootPart") or Character:WaitForChild("HumanoidRootPart")
local StandMorph = Character:FindFirstChild("StandMorph")
local RemoteEvent = Character:FindFirstChild("RemoteEvent") or Character:WaitForChild("RemoteEvent")
local RemoteFunction = Character:FindFirstChild("RemoteFunction") or Character:WaitForChild("RemoteFunction")
local CurrentCamera = workspace.CurrentCamera
local PlayerGui = Player:FindFirstChild("PlayerGui")

--// Services
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local TeleportService = game:GetService("TeleportService")

--// Ignore these
local TempStore = Instance.new("Folder", game.ReplicatedStorage)
TempStore.Name = "TempStorage"
local StayInPilot = Instance.new("BoolValue", workspace)
StayInPilot.Value = false

--[[
        disables effects so crasher doesnt brick your game
 
for i,v in getconnections(game.ReplicatedStorage.ClientFX.OnClientEvent) do
    v:Disable()
end

]]

getgenv().settings = {
    ["cachedbodyparts"] = {},
    ["noclip"] = false,
    ["invisenabled"] = nil,
    ["antits"] = nil,
    ["inviskey"] = Enum.KeyCode.L,
    ["oldpos"] = nil,
    ["delay"] = 0.8,
    ["crasher"] = false,
    ["customval"] = 2000,
    ["standspeed"] = 1.5,
    ["pilotjumppower"] = 1.5,
    ["hidebody"] = true,
    ["tpbodytostand"] = true,
    ["bodydistance"] = 37,
    ["pilotkey"] = Enum.KeyCode.H,
    ["currentargs"] = nil,
    ["flingtarget"] = nil,
    ["animationlist"] = {},
    ["1"] = nil,
    ["2"] = nil,
    ["3"] = nil,
    ["4"] = nil,
    ["5"] = nil,
    ["6"] = nil,
    ["7"] = nil,
    ["8"] = nil,
    ["9"] = nil,
    ["target"] = nil,
    ["attach"] = false,
    ["distancefr"] = 2,
    ["god"] = nil,
    ["kidnaptarget"] = nil,
    ["teleportpos"] = CFrame.new(0, -500, 0),
    ["movementpredictionstrength"] = 0.35,
    ["timeout"] = 1,
    ["useinvis"] = true
}

settings.teleports = {
    ["Newbie Giorno"] = CFrame.new(1, 0, -697),
    ["Train Station Side 1"] = CFrame.new(-214, 0, 18),
    ["Train Station Side 2"] = CFrame.new(-265, -30, -447),
    ["Pizza Place"] = CFrame.new(113, 6, 71),
    ["The Arcade"] = CFrame.new(255, 5, -239),
    ["The Cafe"] = CFrame.new(-544, -25, -174),
    ["Diavolo"] = CFrame.new(1126, 116, -129),
    ["Dio P3"] = CFrame.new(-44, 0, -973),
    ["Jotaro P3"] = CFrame.new(182, -25, 578),
    ["Jotaro P6"] = CFrame.new(784, -42, 144),
    ["Tallest Peak"] = CFrame.new(-237, 284, 305),
    ["Hamon Merchant"] = CFrame.new(421, 8, -287),
    ["Boxing Merchant"] = CFrame.new(281, 0, 101),
    ["Pluck Merchant"] = CFrame.new(125, -27, 438),
    ["Heaven Dimension"] = CFrame.new(8553, -479, 8154),
    ["Arrowsmith"] = CFrame.new(-667, 16, -299),
    ["Cosmetics Merchants"] = CFrame.new(512, 2, 22),
    ["Leaky Eye Luca"] = CFrame.new(-382, 0, -711),
    ["Chad"] = CFrame.new(-121, -24, 524),
    ["Brad the Bat Merchant"] = CFrame.new(-14, -0, -286),
    ["Dracula"] = CFrame.new(-420, -34, -75),
    ["Kars"] = CFrame.new(264, -33, 112),
    ["Homeless Man Jill"] = CFrame.new(-142, -31, -577),
    ["Vampire Room"] = CFrame.new(391, -31, -166),
    ["Enrico Pucci"] = CFrame.new(917, 34, -17),
    ["Safe Spot"] = CFrame.new(-452, -20, 206)
}

for i,v in game.ReplicatedStorage.Anims:GetDescendants() do
    if v:IsA("Animation") and v.Parent.Name ~= "Poses" then
        table.insert(settings["animationlist"], v.Name)
    end
end

if workspace:FindFirstChild("AnticheatBypass") == nil then
    hookfunction(workspace.Raycast, function() -- noclip bypass
        return
    end)

    local OldNamecallTP;
    OldNamecallTP = hookmetamethod(game, '__namecall', newcclosure(function(self, ...)
        local Arguments = {...}
        local Method =  getnamecallmethod()
            
        if Method == "InvokeServer" and Arguments[1] == "idklolbrah2de" then
            return "  ___XP DE KEY"
        end
            
        return OldNamecallTP(self, ...)
    end))
end

if workspace:FindFirstChild("AnticheatBypass") ~= nil then
    workspace.AnticheatBypass:Destroy()
end

local DontTouch = Instance.new("Part", workspace)
DontTouch.Transparency = 1
DontTouch.Anchored = true
DontTouch.CanCollide = false
DontTouch.Name = "AnticheatBypass"

local function SearchPlayer(Name)
    local ClosestMatch = nil
    local ClosestLetters = 0
    for i,v in workspace.Living:GetChildren() do
        local matched_letters = 0
        for i = 1, #Name do
            if string.sub(Name:lower(), 1, i) == string.sub(v.Name:lower(), 1, i) then
                matched_letters = i
            end
        end
        if matched_letters > ClosestLetters then
            ClosestLetters = matched_letters
            ClosestMatch = v
        end
    end
    return ClosestMatch
end

local function UpdateIndex()
	CurrentCharacter = Player.Character
	Humanoid = CurrentCharacter:FindFirstChild("Humanoid") or CurrentCharacter:WaitForChild("Humanoid")
	SummonedStand = CurrentCharacter:FindFirstChild("SummonedStand") or CurrentCharacter:WaitForChild("SummonedStand")
	
	StandMorph = CurrentCharacter:FindFirstChild("StandMorph")
	StandHumanoid = StandMorph:FindFirstChild("AnimationController") or StandMorph:WaitForChild("AnimationController")
	
	Camera = workspace.CurrentCamera
end	


local function PilotStand()
	UpdateIndex()
	
	for i,v in workspace.Locations:GetChildren() do
		if v.Name == "Naples' Sewers" then
			v.Parent = TempStore
		end
	end

	local CameraValue = Instance.new("ObjectValue", StandMorph.Parent)
	local PilotFunctions = {["FocusCam"] = CameraValue, ["CFrame"] = CurrentCharacter.PrimaryPart.CFrame}

	CameraValue.Name = "FocusCam"
	CameraValue.Value = StandHumanoid
	
	for _,v in CurrentCharacter:GetChildren() do
		if v:IsA("BasePart") then
			v.CanCollide = false
		end
	end
	
	--//Jumping\\--
	PilotFunctions["JumpSignal"] = Humanoid:GetPropertyChangedSignal("Jump"):Connect(function()
		if Humanoid.Jump then
	    	StandHumanoid.Jump = true
	    end
	end)
	
	--//WalkSpeed\\--
	StandHumanoid.WalkSpeed = Humanoid.WalkSpeed*settings["standspeed"]
	PilotFunctions["PilotSpeed"] = Humanoid:GetPropertyChangedSignal("WalkSpeed"):Connect(function()
	    StandHumanoid.WalkSpeed = Humanoid.WalkSpeed*settings["standspeed"]
	end)
	
	
	--//Jump Power\\--
	StandHumanoid.JumpPower = Humanoid.JumpPower*settings["pilotjumppower"]
	PilotFunctions["JumpPower"] = Humanoid:GetPropertyChangedSignal("JumpPower"):Connect(function()
	    StandHumanoid.JumpPower = Humanoid.JumpPower*settings["pilotjumppower"]
	end)
	
	if not settings["hidebody"] then
		CurrentCharacter.PrimaryPart.Anchored = true
	end
	
	--//Walking\\--
	PilotFunctions["LoopTP"] = RunService.Heartbeat:Connect(function()
		local MoveDirection = Camera.CFrame:VectorToObjectSpace(Humanoid.MoveDirection)
		StandHumanoid:Move(MoveDirection, true)
		
		if settings["hidebody"] then
			CurrentCharacter.PrimaryPart.CFrame = StandMorph.PrimaryPart.CFrame+Vector3.new(0,-settings["bodydistance"],0)
		end
	end)
	
	StandMorph:FindFirstChild("AlignOrientation", true).Enabled = false
	StandMorph:FindFirstChild("AlignPosition", true).Enabled = false
	for i,v in StandMorph:GetDescendants() do
	    if v:IsA("BasePart") or v:IsA("UnionOperation") then
	        game:GetService("PhysicsService"):SetPartCollisionGroup(v, "Players")
	    end
	end
	return PilotFunctions
end

local function UnPilotStand(Returned)
	UpdateIndex()
	
	for i,v in game.ReplicatedStorage.TempStorage:GetChildren() do
		if v.Name == "Naples' Sewers" then
			v.Parent = workspace.Locations
		end
	end

	for x,v in Returned do
		if tostring(v) == "Connection" then
			v:Disconnect()
		end
	end
	
	Returned["FocusCam"]:Destroy()
	
	CurrentCharacter.PrimaryPart.Velocity = Vector3.new()
	if settings["tpbodytostand"] then
		CurrentCharacter.PrimaryPart.CFrame = StandMorph.PrimaryPart.CFrame
	else
		CurrentCharacter.PrimaryPart.CFrame = Returned["CFrame"]
	end
	
	StandMorph:FindFirstChild("AlignOrientation", true).Enabled = true
	StandMorph:FindFirstChild("AlignPosition", true).Enabled = true
	for i,v in StandMorph:GetDescendants() do
	    if v:IsA("BasePart") or v:IsA("UnionOperation") then
	        game:GetService("PhysicsService"):SetPartCollisionGroup(v, "Stands")
	    end
	end
	
	if not settings["hidebody"] then
		CurrentCharacter.PrimaryPart.Anchored = false
	end
end

local UndergroundAnimation, Highlight
function PlayAnimation(HumanoidCharacter, AnimationID, AnimationSpeed, Time)
    HumanoidCharacter = Character
	local CreatedAnimation = Instance.new("Animation")
	CreatedAnimation.AnimationId = AnimationID
	local HumanoidEx = HumanoidCharacter:FindFirstChild("Humanoid")
	
	if not HumanoidEx then
	    repeat task.wait() until HumanoidCharacter:FindFirstChild("Humanoid")
	    HumanoidEx = HumanoidCharacter:FindFirstChild("Humanoid")
	end
	
	local AnimatorEx = HumanoidEx:FindFirstChild("Animator") or HumanoidEx:WaitForChild("Animator", 3)
    local animationTrack = AnimatorEx:LoadAnimation(CreatedAnimation)

	animationTrack:Play()
	animationTrack:AdjustSpeed(AnimationSpeed)
	animationTrack.Priority= Enum.AnimationPriority.Action4
	animationTrack.TimePosition = Time
	return animationTrack
end

local function Invisibile()
    local HUD = PlayerGui:FindFirstChild("HUD")
    if HUD then
        HUD.Parent = game:GetService("StarterGui")
    else
        local S1, F1 = pcall(function()
            game:GetService("StarterGui"):FindFirstChild("HUD").Parent = PlayerGui
            HUD = PlayerGui:FindFirstChild("HUD")
        end)
        
        print(S1, F1)
    end

    --//As Simple As That Gang\\--
    UndergroundAnimation = PlayAnimation(Character, "rbxassetid://7189062263", 0, 5)
    Player.Character = nil

    UndergroundAnimation:Stop()
    Player.Character = Character
    
    local Survived, Died = pcall(function()
        HUD.Parent = PlayerGui
    end)
    
    print(Survived, Died)
    
    Highlight = Instance.new("Highlight")
    Highlight.Parent = Character
    Highlight.Enabled = true
end

local function Uninvisible()
    --//As Simple As That Gang\\--
    PlayAnimation(Character, "rbxassetid://7189062263", 0, 5):Stop()
    Highlight:Destroy()
end

local function MakeInvisible(character)
    for _, part in character:GetDescendants() do
        if part:IsA("BasePart") or part:IsA("Decal") then
            part.Transparency = 1
            if part:IsA("BasePart") then
                part.CanCollide = false
            end
        elseif part:IsA("ParticleEmitter") or part:IsA("Trail") then
            part.Enabled = false
        elseif part:IsA("BillboardGui") or part:IsA("SurfaceGui") then
            part.Enabled = false
        end
    end
end

local function ControlHumanoid(NPC, WalkSpeed)
    local ControlHumanoid = NPC:FindFirstChild("Humanoid")
    local ControlHumanoidRootPart = NPC:FindFirstChild("HumanoidRootPart")
	ControlHumanoid.WalkSpeed = WalkSpeed
	
	--//Jumping\\--
	Humanoid:GetPropertyChangedSignal("Jump"):Connect(function()
		if not Humanoid.Jump then return end
	    ControlHumanoid.Jump = true
	end)
	
	--//WalkSpeed\\--
	ControlHumanoid.WalkSpeed = Humanoid.WalkSpeed
	Humanoid:GetPropertyChangedSignal("WalkSpeed"):Connect(function()
	    if Humanoid.WalkSpeed == 0 then return end
	    ControlHumanoid.WalkSpeed = Humanoid.WalkSpeed
	end)
    
    --//Walking\\--
    settings["god"] = RunService.Heartbeat:Connect(function()
    	local MoveDirection = CurrentCamera.CFrame:VectorToObjectSpace(Humanoid.MoveDirection)
    	ControlHumanoid:Move(MoveDirection, true)
    	
    	HumanoidRootPart.CFrame = ControlHumanoidRootPart.CFrame
    end)
end

local function ToggleStand()
    RemoteFunction:InvokeServer("ToggleStand", "Toggle")
end

local function AttemptKidnap()
    print(settings["kidnaptarget"], settings["timeout"], settings["movementpredictionstrength"], settings["useinvis"])
    --//Pulling Out Stand\\--
    if not Character:FindFirstChild("SummonedStand") then
        repeat task.wait() ToggleStand() until Character:FindFirstChild("SummonedStand").Value
        StandMorph = Character:FindFirstChild("StandMorph")
    end

    if settings["useinvis"] then Invisibile() end
    local OldCFrame = HumanoidRootPart.CFrame

    --//Already In Room\\--
    if workspace.Living[settings["kidnaptarget"]]:FindFirstChild("InCocoJumbo", settings["timeout"]) then return end

    local TargetHumanoidRootPart = workspace.Living[settings["kidnaptarget"]]:FindFirstChild("HumanoidRootPart")
    local PredictedPosition = TargetHumanoidRootPart.Position + TargetHumanoidRootPart.Velocity * settings["movementpredictionstrength"]
    
    RemoteEvent:FireServer("InputBegan", {["Input"] = Enum.KeyCode.E, ["HoldW"] = true})
    
    local TeleportLoop = RunService.RenderStepped:Connect(function()
        HumanoidRootPart.Velocity = Vector3.new()
        HumanoidRootPart.CFrame = CFrame.new(PredictedPosition)
    end)

    workspace.Living[settings["kidnaptarget"]]:WaitForChild("InCocoJumbo", settings["timeout"])
    TeleportLoop:Disconnect()

    HumanoidRootPart.CFrame = OldCFrame
end

local function LetOutPlayer(CFrame)
    local OldCFrame = HumanoidRootPart.CFrame

    local TeleportLoop = RunService.PreRender:Connect(function()
        --//Not In Room\\--
        if not workspace.Living[settings["kidnaptarget"]]:FindFirstChild("InCocoJumbo") then return end

        HumanoidRootPart.Velocity = Vector3.new()
        HumanoidRootPart.CFrame = CFrame
        RemoteEvent:FireServer("InputBegan", {["Input"] = Enum.KeyCode.Z, ["HoldW"] = true})
    end)

    repeat task.wait() until not workspace.Living[settings["kidnaptarget"]] or not workspace.Living[settings["kidnaptarget"]]:FindFirstChild("InCocoJumbo")
    TeleportLoop:Disconnect()

    HumanoidRootPart.CFrame = OldCFrame
    if settings["useinvis"] then Uninvisible() end
end

MainTab:Keybind("Toggle UI", Enum.KeyCode.RightShift, {"W", "A", "S", "D", "Up", "Down", "Left", "Right", "CapsLock", "Tab"}, function(key)
	if key then
		MainTab:Notification("Changed Toggle key to: ", key)
	else
		Window:ToggleUI()
	end
end)

MainTab:Seperator()

MainTab:Toggle("Invisibility", "makes you invis", false, function(t)
    if t then
        local IsInvisibile
        settings["invisenabled"] = UserInputService.InputBegan:Connect(function(Input, GameProccessed)
            if GameProccessed then return end
            if Input.KeyCode ~= settings["inviskey"] then return end
        
            if IsInvisibile then
                Uninvisible()
            else
                Invisibile()
            end
        
            IsInvisibile = not IsInvisibile
        end)
    else
        if settings["invisenabled"] then
            settings["invisenabled"]:Disconnect()
            Uninvisible()
        end
    end
end)

settings["7"] = MainTab:TextBox("Invisibility Key", function(text)
    settings["inviskey"] = Enum.KeyCode[text:upper()]
end)

MainTab:Toggle("Godmode", "makes you god", false, function(t)
    if t then
        Character.Archivable = true
        local ControlCharacter = Character:Clone()
        ControlCharacter.Parent = workspace

        if not ControlCharacter:FindFirstChild("HumanoidRootPart") then
            repeat task.wait() until ControlCharacter:FindFirstChild("HumanoidRootPart")
        end
        
        ControlCharacter:FindFirstChild("HumanoidRootPart").CFrame = ControlCharacter:FindFirstChild("HumanoidRootPart").CFrame
        
        MakeInvisible(ControlCharacter)
        ControlHumanoid(ControlCharacter, WalkSpeed)
        RemoteEvent:FireServer("Poison", {Duration = math.huge, TotalDamage = math.huge})
    else
        if settings["god"] then
            workspace:FindFirstChild(Player.Name):Destroy()
            settings["god"]:Disconnect()
            Humanoid.Health = 0
        end
    end
end)

MainTab:Seperator()

MainTab:Toggle("No-Clip", "noclip", false, function(t)
    settings["noclip"] = t
    if settings["noclip"] then
        
        if Character then
            --while settings["noclip"] do task.wait()
                for i,v in Character:GetChildren() do
                    if v:IsA("BasePart") and v.CanCollide then
                        table.insert(settings["cachedbodyparts"], v.Name)
                        v.CanCollide = false 
                    end  
                end
            --end
        end
    else
        for i,v in settings["cachedbodyparts"] do
            Character[v].CanCollide = true
        end
    end
end, "Enables noclip (or disables)")

MainTab:Seperator()

MainTab:Toggle("Player Crasher/Server Lagger", "crashes everyone", false, function(t)
    settings["crasher"] = t
    if settings["crasher"] then
        while settings["crasher"] do task.wait()
			for i = settings["customval"], 1, -1 do
				Character.RemoteEvent:FireServer("Poison", {Duration = 10000, TotalDamage = 0.0001})
				Character.RemoteEvent:FireServer("Bleed", {Duration = 10000, TotalDamage = 0.0001})
			end
		end
    else
		task.wait(1)
		Character.RemoteEvent:FireServer("StopPoison")
		Character.RemoteEvent:FireServer("StopBleed")
    end
end)

MainTab:Slider("Player Crasher Strength", 0, 50000, 2000, function(t)
	settings["customval"] = t
end)

MainTab:Seperator()

MainTab:Toggle("Anti-Timestop", "Bypasses timestop", false, function(t)
	if t then
		settings["antits"] = workspace.Living.DescendantAdded:Connect(function(a)
			if a.Name == "TimeStopping" then
				if Player:DistanceFromCharacter(workspace.Living[tostring(a.Parent)].HumanoidRootPart.Position) < 25 then
					oldpos = Character.PrimaryPart.CFrame
					task.wait(0.1)
					Character.PrimaryPart.CFrame += Vector3.new(800,1000,500)
					task.wait(settings["delay"])
					Character.PrimaryPart.CFrame = oldpos
					print("hiu")
				else
					return
				end
			end
		end)
	else
		settings["antits"]:Disconnect()
	end
end)

MainTab:Slider("Anti-Timestop Delay", 0, 2, 0.8, function(t)
	settings["delay"] = t
end)

StandTab:Toggle("Control Stand (God/Invis/Anti-Stun)", "yes", false, function(t)
	if t then
		repeat task.wait() until Character:FindFirstChild("StandMorph")
		UpdateIndex()
		settings["1"] = SummonedStand:GetPropertyChangedSignal("Value"):Connect(function()
			if not SummonedStand.Value then
				StayInPilot.Value = false
			end
		end)

		settings["2"] = UserInputService.InputBegan:Connect(function(InputObject)
			if UserInputService:GetFocusedTextBox() then
				return
			end

			if InputObject.KeyCode == settings["pilotkey"] then
				StayInPilot.Value = not StayInPilot.Value
			end
		end)

		settings["3"] = StayInPilot:GetPropertyChangedSignal("Value"):Connect(function()
			if StayInPilot.Value then
				settings["currentargs"] = PilotStand()
			else
				UnPilotStand(settings["currentargs"])
			end
		end)
	else
		settings["1"]:Disconnect()
		settings["2"]:Disconnect()
		settings["3"]:Disconnect()
		UnPilotStand(settings["currentargs"])
	end
end)

StandTab:Slider("Pilot Walk Speed", 1, 25, 1.5, function(t)
	settings["standspeed"] = t
end)

StandTab:Slider("Pilot Jump Power", 1, 50, 1.5, function(t)
	settings["pilotjumppower"] = t
end)

StandTab:Slider("Body distance from stand", 5, 45, 37, function(t)
	settings["bodydistance"] = t
end)

StandTab:Toggle("Hide Body", "self explanatory", true, function(t)
    settings["hidebody"] = t
end)

StandTab:Toggle("TP Body to Stand", "self explanatory", true, function(t)
    settings["tpbodytostand"] = t
end)

settings["4"] = StandTab:TextBox("Pilot Key", function(text)
    settings["pilotkey"] = Enum.KeyCode[text:upper()]
end)

StandTab:Seperator()

settings["5"] = StandTab:TextBox("Choose Fling Target", function(text)
    pcall(function()
        local PossiblePlayer = SearchPlayer(text)
    
        if PossiblePlayer then
            settings["flingtarget"] = PossiblePlayer.Name
            settings["5"]:Update(PossiblePlayer.Name)
        end
    end)
end)

StandTab:Button("Beachboy Fling (Requires Auto Rod Pull)", "flings a player", function(t)
    local Enemy = settings["flingtarget"]
    local EnemyHRP = workspace.Living[Enemy].PrimaryPart
    local CustomBreak;
    local OldCFrame = Character.PrimaryPart.CFrame
    Character.PrimaryPart.CFrame = CFrame.new(10000,1000,10000)
    local FocusCam = Instance.new("ObjectValue", Character)
    FocusCam.Name = "FocusCam"
    FocusCam.Value = EnemyHRP
    
    repeat task.wait()
        Character.PrimaryPart.CFrame = EnemyHRP.CFrame + Vector3.new(0,5,0) - EnemyHRP.Parent.Head.CFrame.LookVector * 5
        task.spawn(function()
            task.wait(0.5)
            CustomBreak = true
        end)
    until CustomBreak
    CustomBreak = false
    
    Character.PrimaryPart.CFrame = EnemyHRP.CFrame + Vector3.new(0,5,0) - EnemyHRP.Parent.Head.CFrame.LookVector * 5
    Character.RemoteEvent:FireServer("InputBegan", {["Input"] = Enum.KeyCode.Y})
    
    repeat task.wait()
        Character.PrimaryPart.CFrame = EnemyHRP.CFrame + Vector3.new(9999,-130,9999) - EnemyHRP.Parent.Head.CFrame.LookVector * 30
        task.spawn(function()
            task.wait(1)
            CustomBreak = true
        end)
    until CustomBreak
    
    CustomBreak = false
    Character.PrimaryPart.CFrame = OldCFrame
    task.wait(2)
    FocusCam:Destroy()
end)

StandTab:Seperator()

StandTab:Toggle("Use Invis for Mr.Pres", "yes", true, function(t)
    if t then
        settings["useinvis"] = t
    end
end)

StandTab:Slider("Movement Prediction Strength", 0, 0.95, 0.35, function(t)
    settings["movementpredictionstrength"] = t
end)
    
StandTab:Slider("Teleport Timeout", 1, 5, 1, function(t)
    settings["timeout"] = t
end)

settings["9"] = StandTab:TextBox("Mr. Pres Target Player", function(text)
    pcall(function()
        local PossiblePlayer = SearchPlayer(text)
    
        if PossiblePlayer then
            settings["kidnaptarget"] = PossiblePlayer.Name
            settings["9"]:Update(PossiblePlayer.Name)
        end
    end)
end)

StandTab:Button("Mr.Pres Kidnap+Kill", "kidnap someone", function(t)
    AttemptKidnap()
    LetOutPlayer(settings["teleportpos"])
end)

StandTab:Seperator()

StandTab:Dropdown("Stand & Spec Animations", settings["animationlist"], function(SelectedAnimation)
    local StandMorph = StandMorph
    local AnimID = 0
    for i,v in game.ReplicatedStorage.Anims:GetDescendants() do
        if v:IsA("Animation") and v.Name == SelectedAnimation then
            AnimID = v.AnimationId
            break
        end
    end

    local Anim = Instance.new("Animation", workspace.AnticheatBypass); Anim.Name = "YBA_AnticheatDetection"; Anim.AnimationId = AnimID
    local Anim2 = StandMorph.AnimationController:LoadAnimation(Anim)
    Anim2:Play()
end)

settings["6"] = TeleportTab:TextBox("TP to Player", function(text)
    pcall(function()
        local PossiblePlayer = SearchPlayer(text)
    
        if PossiblePlayer then
            settings["6"]:Update(PossiblePlayer.Name)
            Character.PrimaryPart.CFrame = PossiblePlayer.PrimaryPart.CFrame
            if StandMorph then
                StandMorph.PrimaryPart.CFrame = PossiblePlayer.PrimaryPart.CFrame
            end
        end
    end)
end)

for place, cframe in settings.teleports do
    TeleportTab:Button(place, place, function()
        Character.PrimaryPart.CFrame = cframe
        if Character:FindFirstChild("StandMorph") and StandMorph:FindFirstChild("HumanoidRootPart") then
            StandMorph.PrimaryPart.CFrame = cframe
        end
    end)
end

ServerTab:Button("Rejoin Server", "yes", function()
    TeleportService:Teleport(game.PlaceId, game.Players.LocalPlayer)
end)

settings["8"] = OtherTab:TextBox("Attach Target Player", function(text)
    pcall(function()
        local PossiblePlayer = SearchPlayer(text)
    
        if PossiblePlayer then
            settings["target"] = PossiblePlayer.Name
            settings["8"]:Update(PossiblePlayer.Name)
        end
    end)
end)

OtherTab:Toggle("Attach Stand to Player", "yes", false, function(t)
    settings["attach"] = t
    while settings["attach"] do task.wait()
        if not Character or not StandMorph then return end
        StandMorph.PrimaryPart.CFrame = workspace.Living[settings["target"]].PrimaryPart.CFrame - workspace.Living[settings["target"]].PrimaryPart.CFrame.LookVector * settings["distancefr"]
    end
end)

OtherTab:Slider("Distance", -10, 8, 2, function(t)
    settings["distancefr"] = t
end)
