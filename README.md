# LibBlzSettings

## 案例

这里有两个这个库的使用案例可供参考:
- [SanluliUtils/Settings.lua](https://github.com/Sanluli36li/SanluliUtils/blob/main/Settings.lua)
- [ItemInfoOverlay/Settings.lua](https://github.com/Sanluli36li/ItemInfoOverlay/blob/main/Settings.lua)

## 关于暴雪设置界面本身的缺陷

事实上，暴雪提供的Settings API仍然有非常多缺陷，尤其是没有直接定义在`Settings`中，但被应用于选项中的复合控件  
由于设置界面是完全静态的，一些暴雪选项没有使用到的情况可能会有问题，包括:  
- [x] 带选择框的复合控件的子选项不会随着父选项的变化而变化 (已通过单独创建设置包含settings键的设置项目解决)
- [x] 带选择框的下拉菜单不随父控件的变化而立刻变化，需要重新进入设置页面才会更新 (已通过覆写EvaluateState方法解决)
- [ ] 带按钮的选择框在选择时会触发两次`OnValueChanged`事件(包括两次点击声音，可以听出带按钮选择框的声音明显比其他选择框大)

## 开始

### 创建分类

首先，你需要创建一个表，用于序列化为设置布局

```lua
local category = {
    name = "LibBlzSettingsDemo",
    database = "LibBlzSettingsDB",
    settings = {
        -- 这里将储存设置项
        -- ...
    },
    subCategory = {
        -- 可选
        -- ...
    }
}
```
`name`: `string`类型，将作为显示在`ESC`->`选项`->`插件`里的分类名称, 同时也将作为表头显示  
`settings`: 数组型`table`，储存设置项的表  
`subCategory`: 可选，数组型`table`，子选项页面的表，结构与此表完全相同  
`database`: 可选，用以储存变量的数据库表，将应用到所有设置项和子分类中  
如果是一个`table`类型，变量将直接储存在这个表中  
如果是一个`string`类型，且此名称对应的全局变量是一个`table`类型，变量将储存在这个表中  
**例如:** 你在toc中声明了插件储存的变量
```
## SavedVariables: ItemInfoOverlayDB
```
那么你可以直接使用 `database = "ItemInfoOverlayDB"`  
需要注意的一点是，插件声明的SavedVariables需要在`ADDON_LOADED`事件后才被载入，如果你需要使用此变量，请确保在这个事件或之后才注册设置项目

### 创建设置项



### 注册布局

    

