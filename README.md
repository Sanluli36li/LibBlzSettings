# LibBlzSettings

## Docs:
[Getting Started](https://github.com/Sanluli36li/LibBlzSettings/wiki/Getting-Started)  
[开始使用](https://github.com/Sanluli36li/LibBlzSettings/wiki/%E5%BC%80%E5%A7%8B%E4%BD%BF%E7%94%A8)  

## Examples
Here are two usage examples of this library for reference:

- [SanluliUtils/Settings.lua](https://github.com/Sanluli36li/SanluliUtils/blob/main/Settings.lua)
- [ItemInfoOverlay/Settings.lua](https://github.com/Sanluli36li/ItemInfoOverlay/blob/main/Settings.lua)

## About the Inherent Defects of the Blizzard Settings Interface
In fact, the Settings API provided by Blizzard still has many defects, especially regarding composite controls that are not directly defined in `Settings.lua` but are used in options.
Since the settings interface is completely static, some situations not utilized by Blizzard options may have issues, including:
- [x] Sub-options of composite controls with checkboxes do not change according to the parent option (resolved by individually creating setting items containing the settings key)
- [x] Dropdown menus with checkboxes do not update immediately when the parent control changes; you need to re-enter the settings page for the update to take effect (resolved by overriding the EvaluateState method)
- [ ] Checkboxes with buttons trigger the OnValueChanged event twice when selected (including two click sounds; you can notice that the sound of checkboxes with buttons is significantly louder than other checkboxes)