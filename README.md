# Machina
Fluent, Open Source, Mac-OS themed Gui Library for Roblox.
<img width="1146" height="471" alt="image" src="https://github.com/user-attachments/assets/9ea0061d-d540-4f56-9e0a-1a2b55dba008" />

# Functions:
- Free, Open Source, Under BSD-3 License.
- White and Dark Theme.
- Eye candy level of tweening.
- Resizable, Minimizing and maximizing.
- Decent Codebase.

# Example code, from [there](https://github.com/KadeTheExploiter/Machina/blob/main/Examples/Example.luau)

```luau
-- For Details, check https://github.com/KadeTheExploiter/Machina/DocumentedExample.luau
local HttpRequest = request or http_request or http and http.request or syn and syn.request
local ModuleData = HttpRequest({Method = "GET", Url = "https://raw.githubusercontent.com/KadeTheExploiter/Machina/refs/heads/main/Module.luau"})
local GuiLibrary = loadstring(ModuleData.Body)()

local CustomTheme = GuiLibrary:DefineTheme({MainFrame = Color3.new(12, 12, 12)}, "Dark")
local MainFrame, ScreenGui = GuiLibrary:Load("Gui Name", "Dark") -- If you want to use a custom theme, put the table variable in instead of a string.

print(MainFrame:GetScreenGui().Parent)

local Tabs = {
	Home = MainFrame:NewTabEntry("Home Page", "rbxassetid://12974400533"),
	Information = MainFrame:NewTabEntry("Information")
}

local HomeButton; HomeButton = Tabs.Home:NewButtonEntry("Notify me!", "Notifies you with something.", function()
	game:GetService("StarterGui"):SetCore("SendNotification", {Title = "Notified!"})
	HomeButton:UpdateText("Notified!")

	task.delay(0.25, HomeButton.UpdateText, HomeButton, "Notify me!")
end)

local HomeToggle = Tabs.Home:NewToggleEntry("Hii!!", "Toggle to explode!!", false, function(Bool: boolean)
	print(Bool and "Checked!" or "Unchecked.")
end, false)

HomeToggle:SetReadOnly(true)

local DetectionStatusLabel = Tabs.Home:NewLabelEntry(
	"You won't be detected!", 
	"Detection on all devices!!!", 
	"Positive"
)

DetectionStatusLabel:UpdateEverything("Severe Warning!", "The anti tamper has been triggered.", "Danger")

local TextboxPrinter = Tabs.Home:NewTextboxEntry("Print out your text!", "Simple as that!", function(Text)
	print(Text)
end)

local DropdownItems = {
    {game.Players.LocalPlayer, "LocalPlayer", "Located in Players."},
    {workspace.CurrentCamera, "CurrentCamera", "That's your camera."},
    workspace.Terrain,
    {game.ReplicatedStorage}
}

local HomeDropdown = Tabs.Home:NewDropdownEntry("Instance Selection", "Select Your Instance.", DropdownItems, 1, function(Selected)
	warn("Your choice was:", Selected)
end)

HomeDropdown:UpdateList({{workspace.Terrain, "Bad move...", "All done!"}, 1, {1}, {"1"}, {1, "1", "1"}, 1, "1"})

local ExperienceSlider = Tabs.Home:NewSliderEntry("Select Your Level!", "The bigger the numbers, the harder.", 10, 100, 60, function(Numbers)
	print(Numbers)
end)
```

# Credits:
- GelatekForever: Lead Developer, Everything.
- Babyhamsta: [cloneref](https://docs.sunc.su/Instances/cloneref/) workaround.
