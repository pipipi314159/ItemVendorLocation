# ItemVendorLocation (TW)

> 本分支是 [electr0sheep/ItemVendorLocation](https://github.com/electr0sheep/ItemVendorLocation) 的**台服（繁體中文）客戶端**移植版，供台服 Dalamud（API13）使用。
> **使用上遇到問題請回報到本 repo，不要回報給原作者。**

## 版本資訊

| 項目 | 內容 |
|---|---|
| 基於原版 commit | `8d711d8a27cbe88eede6baf27a19191d449a1211`（2025-08-08，7.3 更新合併，版本 2.11.0.0） |
| Dalamud API | 13（`Dalamud.NET.Sdk/13.0.0`，.NET 9） |
| 分支 | `tw-api13` |

原版之後的 commit（2025-12 起）改用 .NET 10 / API14 以上，台服 Dalamud 無法載入，因此停在這個版本。

## 程式修改

- `Localization.cs`：新增繁中客戶端（`ClientLanguage` 5 / 7）的右鍵選單文字「查找兌換位置」。原版只有簡中，台服會顯示英文。
- `ItemVendorLocation.yaml`：插件名稱加上 `(TW)`，`repo_url` 指向本 repo。`InternalName` 未更動，原有設定可沿用。

其餘程式碼與原版相同。

## 功能說明

- 物品右鍵選單「查找兌換位置」：列出販售該物品的 NPC 與位置，或直接在聊天欄貼出座標。
- 指令 `/pvendor` 開啟設定；`/pvendor 物品名稱` 搜尋物品（不分大小寫，最多 50 筆）。

## 自行編譯

```bat
set DALAMUD_HOME=<台服 Dalamud Injector 資料夾>
dotnet build ItemVendorLocation\ItemVendorLocation.csproj -c Release
```

輸出：`ItemVendorLocation\bin\Release\ItemVendorLocation.dll`，在 `/xlsettings` → 實驗性功能 → 開發插件位置加入此路徑即可載入。

## 原作者與授權

原作者為 electr0sheep 與 [Nuko](https://github.com/NukoOoOoOoO)，以及其他貢獻者。原 repo 未附授權檔案，著作權歸原作者所有；本分支僅為台服相容性移植。

---

以下為原版 README：

# ItemVendorLocation
Adds a context menu to find vendor locations for items that can be purchased from a vendor.
Also adds a chat command that can be used to search for items
`pvendor` opens the configuration window
`pvendor ceruleum tank` searches for an item with "ceruleum tank" in the name. This is not case-sensitive and results are limited
to a maximum of 50.

The plugin provides the following indicators to know if an item is sold by a vendor:
1. The game indicates the shop selling price without any plugins

![Alt text](/Images/GilVendor.png?raw=true "Item Sold for Gil")

2. If the plugin determines an item is sold by a GC vendor, the item's popup will show the price in your GC's currency

![Alt text](/Images/GCVendor.png?raw=true "Item Sold for GC Seals")

3. If the plugin determines an item is sold by other vendors, the item's popup will show that it is sold by Special Vendors

![Alt text](/Images//SpecialVendor.png?raw=true "Item Sold for other currency")

4. If the item is not sold by any vendors, the shop selling price will show None

![Alt text](/Images/NoVendors.png?raw=true "Item not sold for any currency")

If the item is sold by a vendor, a new option will be added to the item's context menu. When clicked, this option can display
results in one of two possible formats.

![Alt text](/Images/ContextMenu.png?raw=true "Item Context Menu")

1. The plugin will show a list of all possible vendors in a plugin GUI window

![Alt text](/Images/VendorLocations.png?raw=true "Vendor Locations")

2. It can simply find the first vendor and link the coordinates in the in-game chat

![Alt text](/Images/ChatVendorLocation.png?raw=true "Vendor Location")

In addition, there is a chat command that can be used i.e. `/pvendor bronze chaser hammer`

# Contributors
I appreciate everyone who has contributed, visible over there to the right.

It would be remiss of me to not give special mention to [Nuko](https://github.com/NukoOoOoOoO) for a near complete rewrite.
They reworked the plugin to completly remove Garland Tools as the data source. This must have taken a ton of work, and is
much appreciated! In addition to this, Nuko continues to maintain and add features to the plugin regularly. Thanks a ton Nuko!