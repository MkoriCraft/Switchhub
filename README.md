if not game:IsLoaded() then 

    repeat game.Loaded:Wait()

    until game:IsLoaded() 

end

repeat wait(1)

    pcall(function()

        if game:GetService("Players").LocalPlayer.PlayerGui.Main:FindFirstChild("ChooseTeam") then

            if game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Visible == true then

                if _G.Team == "Marines" then

                    for i,v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Marines.Frame.ViewportFrame.TextButton.MouseButton1Click)) do

                        v.Function()

                    end

                else

                    for i,v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Pirates.Frame.ViewportFrame.TextButton.MouseButton1Click)) do

                        v.Function()

                    end

                end

            end

        end

    end)

until game.Players.localPlayer.Neutral == false

if _G.Fast_Delay == nil then

	_G.Fast_Delay = 0.3

end

spawn(function()

    while true do wait()

        getgenv().rejoin = game:GetService("CoreGui").RobloxPromptGui.promptOverlay.ChildAdded:Connect(function(Kick)

            if not _G.TP_Ser and _G.Rejoin then

                if Kick.Name == 'ErrorPrompt' and Kick:FindFirstChild('MessageArea') and Kick.MessageArea:FindFirstChild("ErrorFrame") then

                    game:GetService("TeleportService"):Teleport(game.PlaceId)

                    wait(50)

                end

            end

        end)

    end

end)

local VirtualUser=game:service'VirtualUser'

game:service'Players'.LocalPlayer.Idled:connect(function()

	VirtualUser:CaptureController()

	VirtualUser:ClickButton2(Vector2.new())

end)

spawn(function()

	while wait(3) do

		game:GetService'VirtualUser':CaptureController()

	end

end)

Old_World = false

New_World = false

Three_World = false

local placeId = game.PlaceId

if placeId == 2753915549 then

    Old_World = true

elseif placeId == 4442272183 then

    New_World = true

elseif placeId == 7449423635 then

    Three_World = true

end

_G.Color = Color3.fromRGB(68, 202, 186)

_G.Setting_table = {

    Auto_Farm = false,

    FastAttack = true,

	Auto_Buso = true,

	Auto_Ken = true,

	Show_Damage = true,

	NoClip = true,

	Save_Member = true,

	Melee_A = true,

	Defense_A = true,

	SkillZ = true,

	Rejoin = true,

	Anti_AFK = true,

	K_MAX = 50,

	Chest_Lock = 50,

	Delay_C = 15

}

_G.Check_Save_Setting = "CheckSaveSetting"

getgenv()['JsonEncode'] = function(msg)

    return game:GetService("HttpService"):JSONEncode(msg)

end

getgenv()['JsonDecode'] = function(msg)

    return game:GetService("HttpService"):JSONDecode(msg)

end

getgenv()['Check_Setting'] = function(Name)

    if not _G.Dis and not isfolder('Switch Hub BF Premium') then

        makefolder('Switch Hub BF Premium')

    end

    if not _G.Dis and not isfile('Switch Hub BF Premium/'..Name..'.json') then

        writefile('Switch Hub BF Premium/'..Name..'.json',JsonEncode(_G.Setting_table))

    end

end

getgenv()['Get_Setting'] = function(Name)

    if not _G.Dis and isfolder('Switch Hub BF Premium') and isfile('Switch Hub BF Premium/'..Name..'.json') then

        _G.Setting_table = JsonDecode(readfile('Switch Hub BF Premium/'..Name..'.json'))

        return _G.Setting_table

	elseif not _G.Dis then

        Check_Setting(Name)

    end

end

getgenv()['Update_Setting'] = function(Name)

    if not _G.Dis and isfolder('Switch Hub BF Premium') and isfile('Switch Hub BF Premium/'..Name..'.json') then

        writefile('Switch Hub BF Premium/'..Name..'.json',JsonEncode(_G.Setting_table))

	elseif not _G.Dis then

        Check_Setting(Name)

    end

end

Check_Setting(_G.Check_Save_Setting)

Get_Setting(_G.Check_Save_Setting)

if _G.Setting_table.Save_Member then

	getgenv()['MyName'] = game.Players.LocalPlayer.Name

	print("Save Member")

elseif _G.Setting_table.Save_All_Member then

	getgenv()['MyName'] = "AllMember"

	print("Save All Member")

else

	getgenv()['MyName'] = "None"

	_G.Dis = true

end

Check_Setting(getgenv()['MyName'])

Get_Setting(getgenv()['MyName'])

_G.Setting_table.Key = _G.wl_key

Update_Setting(getgenv()['MyName'])

if type(_G.Setting_table.Weapon) ~= 'string' then

	for i2,v2 in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  

		if tostring(v2.ToolTip) == "Melee" then

			_G.Setting_table.Weapon = v2.Name

		end

	end

end

function Text(value)

    game.StarterGui:SetCore("SendNotification", {

        Title = "Switch Notification", 

        Text = tostring(value),

        Icon = "http://www.roblox.com/asset/?id=9606070311",

        Duration = 10

    })

end

function Com()

    game.StarterGui:SetCore("SendNotification", {

        Title = "Switch Notification", 

        Text = "✅  Complete",

        Icon = "http://www.roblox.com/asset/?id=9606070311",

        Duration = 5

    })

end

function TelePBoss(p)

	if (p.Position-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude >= 2000 and not Auto_Raid and game.Players.LocalPlayer.Character.Humanoid.Health > 0 then

		if NameQuest == "FishmanQuest" then

			_G.Stop_Tween = true

			TP(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame)

			wait(.5)

			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))

			_G.Stop_Tween = nil

		elseif Ms == "God's Guard [Lv. 450]"  then

			_G.Stop_Tween = true

			TP(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame)

			wait(.5)

			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))

			_G.Stop_Tween = nil

		elseif NameQuest == "SkyExp1Quest" then

			_G.Stop_Tween = true

			TP(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame)

			wait(.5)

			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))

			_G.Stop_Tween = nil

		elseif NameQuest == "ShipQuest1" then

			_G.Stop_Tween = true

			TP(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame)

			wait(.5)

			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))

			_G.Stop_Tween = nil

		elseif NameQuest == "ShipQuest2" then

			_G.Stop_Tween = true

			TP(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame)

			wait(.5)

			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))

			_G.Stop_Tween = nil

		elseif NameQuest == "FrostQuest" then

			_G.Stop_Tween = true

			TP(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame)

			wait(.5)

			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-6508.5581054688, 89.034996032715, -132.83953857422))

			_G.Stop_Tween = nil

		else

			Mix_Farm = true

			_G.Stop_Tween = true

			game.Players.LocalPlayer.Character.Humanoid:ChangeState(15)

			repeat wait(.5)

				game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = p

				wait()

				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")

			until (p.Position-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude < 1500 and game.Players.LocalPlayer.Character.Humanoid.Health > 0

			wait(.5)

			_G.Stop_Tween = nil

			Mix_Farm = nil

		end

	end

end

function CheckQuestBoss()

	-- Old World

		if _G.SelectBoss == "Saber Expert [Lv. 200] [Boss]" then

			MsBoss = "Saber Expert [Lv. 200] [Boss]"

			NameBoss = "Saber Expert"

			CFrameBoss = CFrame.new(-1458.89502, 29.8870335, -50.633564, 0.858821094, 1.13848939e-08, 0.512275636, -4.85649254e-09, 1, -1.40823326e-08, -0.512275636, 9.6063415e-09, 0.858821094)

		elseif _G.SelectBoss == "The Saw [Lv. 100] [Boss]" then

			MsBoss = "The Saw [Lv. 100] [Boss]"

			NameBoss = "The Saw"

			CFrameBoss = CFrame.new(-683.519897, 13.8534927, 1610.87854, -0.290192783, 6.88365773e-08, 0.956968188, 6.98413629e-08, 1, -5.07531119e-08, -0.956968188, 5.21077759e-08, -0.290192783)

		elseif _G.SelectBoss == "Greybeard [Lv. 750] [Raid Boss]" then

			MsBoss = "Greybeard [Lv. 750] [Raid Boss]"

			NameBoss = "Greybeard"

			CFrameBoss = CFrame.new(-4955.72949, 80.8163834, 4305.82666, -0.433646321, -1.03394289e-08, 0.901083171, -3.0443168e-08, 1, -3.17633075e-09, -0.901083171, -2.88092288e-08, -0.433646321)

		elseif _G.SelectBoss == "The Gorilla King [Lv. 25] [Boss]" then

			MsBoss = "The Gorilla King [Lv. 25] [Boss]" 

			NameBoss = "The Gorilla King"

			NameQuestBoss = "JungleQuest"

			QuestLvBoss = 3

			CFrameQBoss = CFrame.new(-1604.12012, 36.8521118, 154.23732, 0.0648873374, -4.70858913e-06, -0.997892559, 1.41431883e-07, 1, -4.70933674e-06, 0.997892559, 1.64442184e-07, 0.0648873374)

			CFrameBoss = CFrame.new(-1223.52808, 6.27936459, -502.292664, 0.310949147, -5.66602516e-08, 0.950426519, -3.37275488e-08, 1, 7.06501808e-08, -0.950426519, -5.40241736e-08, 0.310949147)

			TelePBoss(CFrameBoss)

		elseif _G.SelectBoss == "Bobby [Lv. 55] [Boss]" then

			MsBoss = "Bobby [Lv. 55] [Boss]"

			NameBoss = "Bobby"

			NameQuestBoss = "BuggyQuest1"

			QuestLvBoss = 3

			CFrameQBoss = CFrame.new(-1139.59717, 4.75205183, 3825.16211, -0.959730506, -7.5857054e-09, 0.280922383, -4.06310328e-08, 1, -1.11807175e-07, -0.280922383, -1.18718916e-07, -0.959730506)

			CFrameBoss = CFrame.new(-1147.65173, 32.5966301, 4156.02588, 0.956680477, -1.77109952e-10, -0.29113996, 5.16530874e-10, 1, 1.08897802e-09, 0.29113996, -1.19218679e-09, 0.956680477)

			TelePBoss(CFrameBoss)

		elseif _G.SelectBoss == "Yeti [Lv. 110] [Boss]" then

			MsBoss = "Yeti [Lv. 110] [Boss]"

			NameBoss = "Yeti"

			NameQuestBoss = "SnowQuest"

			QuestLvBoss = 3

			CFrameQBoss = CFrame.new(1384.90247, 87.3078308, -1296.6825, 0.280209213, 2.72035177e-08, -0.959938943, -6.75690828e-08, 1, 8.6151708e-09, 0.959938943, 6.24481444e-08, 0.280209213)

			CFrameBoss = CFrame.new(1221.7356, 138.046906, -1488.84082, 0.349343032, -9.49245944e-08, 0.936994851, 6.29478194e-08, 1, 7.7838429e-08, -0.936994851, 3.17894653e-08, 0.349343032)

			TelePBoss(CFrameBoss)

		elseif _G.SelectBoss == "Mob Leader [Lv. 120] [Boss]" then

			MsBoss = "Mob Leader [Lv. 120] [Boss]"

			NameBoss = "Mob Leader"

			CFrameBoss = CFrame.new(-2848.59399, 7.4272871, 5342.44043, -0.928248107, -8.7248246e-08, 0.371961564, -7.61816636e-08, 1, 4.44474857e-08, -0.371961564, 1.29216433e-08, -0.92824)

		elseif _G.SelectBoss == "Vice Admiral [Lv. 130] [Boss]" then

			MsBoss = "Vice Admiral [Lv. 130] [Boss]"

			NameBoss = "Vice Admiral"

			NameQuestBoss = "MarineQuest2"

			QuestLvBoss = 2

			CFrameQBoss = CFrame.new(-5035.42285, 28.6520386, 4324.50293, -0.0611100644, -8.08395768e-08, 0.998130739, -1.57416586e-08, 1, 8.00271849e-08, -0.998130739, -1.08217701e-08, -0.0611100644)

			CFrameBoss = CFrame.new(-5078.45898, 99.6520691, 4402.1665, -0.555574954, -9.88630566e-11, 0.831466436, -6.35508286e-08, 1, -4.23449258e-08, -0.831466436, -7.63661632e-08, -0.555574954)

			TelePBoss(CFrameBoss)

		elseif _G.SelectBoss == "Warden [Lv. 220] [Boss]" then

			MsBoss = "Warden [Lv. 220] [Boss]"

			NameBoss = "Warden"

			NameQuestBoss = "ImpelQuest"

			QuestLvBoss = 1

			CFrameQBoss = CFrame.new(4851.35059, 5.68744135, 743.251282, -0.538484037, -6.68303741e-08, -0.842635691, 1.38001752e-08, 1, -8.81300792e-08, 0.842635691, -5.90851599e-08, -0.538484037)

			CFrameBoss = CFrame.new(5232.5625, 5.26856995, 747.506897, 0.943829298, -4.5439414e-08, 0.330433697, 3.47818627e-08, 1, 3.81658154e-08, -0.330433697, -2.45289105e-08, 0.943829298)

			TelePBoss(CFrameBoss)

		elseif _G.SelectBoss == "Chief Warden [Lv. 230] [Boss]" then

			MsBoss = "Chief Warden [Lv. 230] [Boss]"

			NameBoss = "Chief Warden"

			NameQuestBoss = "ImpelQuest"

			QuestLvBoss = 2

			CFrameQBoss = CFrame.new(4851.35059, 5.68744135, 743.251282, -0.538484037, -6.68303741e-08, -0.842635691, 1.38001752e-08, 1, -8.81300792e-08, 0.842635691, -5.90851599e-08, -0.538484037)

			CFram
