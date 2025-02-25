## Class: MenuItem

> Magdagdag ng mga aytem sa likas na aplikasyon ng mga menu at konteksto ng mga menu.

Proseso:[Pangunahi](../glossary.md#main-process)

Tingnan ang [`Menu`](menu.md) para sa mga halimbawa.

### `bagong MenuItem(opsyon)`

* `pagpipilian` Bagay 
  * `i-klik` Punsyon (opsyonal) - Ay tatawagin na may `i-klik ang(menuItem, browserWindow, event)` kapag ang aytem ng menu ay na-klik na. 
    * `menuItem`MenuItem
    * `browserWindow` [BrowserWindow](browser-window.md)
    * `kaganapan` kaganapan
  * `role` String (optional) - Can be `undo`, `redo`, `cut`, `copy`, `paste`, `pasteandmatchstyle`, `delete`, `selectall`, `reload`, `forcereload`, `toggledevtools`, `resetzoom`, `zoomin`, `zoomout`, `togglefullscreen`, `window`, `minimize`, `close`, `help`, `about`, `services`, `hide`, `hideothers`, `unhide`, `quit`, `startspeaking`, `stopspeaking`, `close`, `minimize`, `zoom` or `front` - Define the action of the menu item, when specified the `click` property will be ignored. See [roles](#roles).
  * `type` String (opsyonal) - Ay maaaring `normal`, `separator`, `submenu`, `checkbox` o `radio`.
  * `label` String (optional)
  * `sublabel` String (optional)
  * `accelerator` [Accelerator](accelerator.md) (opsyonal)
  * `icon` ([NativeImage](native-image.md) | String) (opsyonal)
  * `enabled` Boolean (opsyonal) - Kung hindi totoo, ang aytem ng menu ay naka-grey out at hindi maki-klik.
  * `visible` Boolean (opsyonal) - Kung hindi totoo, ang aytem ng menu ay lubusang itatago.
  * `checked` Boolean (opsyonal) - Dapat lamang na tinukoy para sa uri ng `checkbox` o `radio` ng mga aytem ng menu.
  * `registerAccelerator` Boolean (optional) - If false, the accelerator won't be registered with the system, but it will still be displayed. Defaults to true.
  * `submenu` (MenuItemConstructorOptions[] | [Menu](menu.md)) (optional) - Should be specified for `submenu` type menu items. If `submenu` is specified, the `type: 'submenu'` can be omitted. If the value is not a [`Menu`](menu.md) then it will be automatically converted to one using `Menu.buildFromTemplate`.
  * `id` String (opsyonal) - Kakaiba sa loob ng nag-iisang menu. Kung tinukoy samakatuwid ito ay maaaring gamitin bilang isang sanggunian sa aytem na ito sa pamamagitan ngkatangian ng posisyon.
  * `before` String[] (optional) - Inserts this item before the item with the specified label. If the referenced item doesn't exist the item will be inserted at the end of the menu. Also implies that the menu item in question should be placed in the same “group” as the item.
  * `after` String[] (optional) - Inserts this item after the item with the specified label. If the referenced item doesn't exist the item will be inserted at the end of the menu.
  * `beforeGroupContaining` String[] (optional) - Provides a means for a single context menu to declare the placement of their containing group before the containing group of the item with the specified label.
  * `afterGroupContaining` String[] (optional) - Provides a means for a single context menu to declare the placement of their containing group after the containing group of the item with the specified label.

### Mga tungkulin

Ang mga tungkulin ay nagpapahintulot sa mga aytem ng menu na may paunang tinukoy na mga katangian.

Ito ang mabisang paraan para matukoy ang `role` para sa kahit anong aytem ng menu na pumaparehas sa standard na tungkulin, sa halip na manu-manong sinusubukang i-implementa ang katangian sa isang punsyon ng `click`. Ang dati ng gawang katangian ng `role` ay magbibigay ng pinakanatural na karanasan.

Ang mga halaga ng `label` at `accelerator` ay opsyonal kapag ginagamit ang`role` at magiging default sa naaangkop na halaga para sa bawat plataporma.

Every menu item must have either a `role`, `label`, or in the case of a separator a `type`.

Ang katangian ng `role` ay maaaring ang mga sumusunod na halaga:

* `undo`
* `redo`
* `cut`
* `kopyahin`
* `paste`
* `pasteAnd MatchStyle`
* `selectAll`
* `delete`
* `minimize` - Paliitin ang kasalukuyang window.
* `close` - Isara ang kasalukuyang window.
* `quit` - Quit the application.
* `reload` - Ikarga ulit ang kasalukuyang window.
* `forceReload` - Reload the current window ignoring the cache.
* `toggleDevTools` - Toggle developer tools in the current window.
* `toggleFullScreen` - Toggle full screen mode on the current window.
* `resetZoom` - Reset the focused page's zoom level to the original size.
* `zoomIn` - Zoom in the focused page by 10%.
* `zoomOut` - Zoom out the focused page by 10%.
* `fileMenu` - Whole default "File" menu (Close / Quit)
* `editMenu` - Ang kabuoang default na menu ng "Edit" (Undo, Kopya, atbp.).
* `viewMenu` - Whole default "View" menu (Reload, Toggle Developer Tools, etc.)
* `windowMenu` - Whole default "Window" menu (Minimize, Zoom, etc.).

The following additional roles are available on *macOS*:

* `appMenu` - Whole default "App" menu (About, Services, etc.)
* `about` - Ibalangkas sa mga aksyon ng `orderFrontStandardAboutPanel`.
* `hide` - Ibalangkas sa mga aksyon ng `hide`.
* `hideOthers` - Map to the `hideOtherApplications` action.
* `unhide` - Ibalangkas sa mga aksyon ng `unhideAllApplications`.
* `startSpeaking` - Map to the `startSpeaking` action.
* `stopSpeaking` - Map to the `stopSpeaking` action.
* `front` - Ibalangkas sa mga aksyon ng `arrangeInFront`.
* `zoom` - Ibalangkas sa mga aksyon ng `performZoom`.
* `toggleTabBar` - Map to the `toggleTabBar` action.
* `selectNextTab` - Map to the `selectNextTab` action.
* `selectPreviousTab` - Map to the `selectPreviousTab` action.
* `mergeAllWindows` - Map to the `mergeAllWindows` action.
* `moveTabToNewWindow` - Map to the `moveTabToNewWindow` action.
* `window` - The submenu is a "Window" menu.
* `help` - The submenu is a "Help" menu.
* `services` - The submenu is a ["Services"](https://developer.apple.com/documentation/appkit/nsapplication/1428608-servicesmenu?language=objc) menu. This is only intended for use in the Application Menu and is *not* the same as the "Services" submenu used in context menus in macOS apps, which is not implemented in Electron.
* `recentDocuments` - The submenu is an "Open Recent" menu.
* `clearRecentDocuments` - Map to the `clearRecentDocuments` action.

When specifying a `role` on macOS, `label` and `accelerator` are the only options that will affect the menu item. All other options will be ignored. Lowercase `role`, e.g. `toggledevtools`, is still supported.

**Nota Bene:** The `enabled` and `visibility` properties are not available for top-level menu items in the tray on MacOS.

### Katangian ng pagkakataon

Ang mga sumusunod na mga katangian ay makukuha sa mga instansya ng `MenuItem`:

#### `ang menuItem.enabled`

Ang isang `Boolean` ay nagpapakita kung ang aytem ay pinagana na, ang katangian na ito ay maaaring mabago ng matindi.

#### `ang menuItem.visible`

Ang isang `Boolean` ay nagpapakita kung ang aytem ay nakikita, ang katangian na ito ay maaaring mabago ng matindi.

#### `ang menuItem.checked`

Ang isang `Boolean` ay nagpapakita kung ang aytem ay nasuri na, ang katangian na ito ay maaaring mabago ng matindi.

Ang isang `checkbox` na aytem ng menu ay ito-toggle ang katangian ng `checked` ng pagbukas at pagpatay kapag napili.

Ang isang `radio` na aytem ng menu ay bubuksan ang kanyang `checked` na katangian kapag na-klik, at papatayin ang nasabing katangian para sa lahat ng mga katabing aytem sa loob ng parehong menu.

Maaari kang magdagdag ng isang punsyon ng `click` para sa karagdagang gawain.

#### `ang menuItem.label`

Ang isang `String` ay kumakatawan sa mga aytem ng menu sa nakikitang tatak.

#### `ang menuItem.click`

Ang isang `Function` na ititira kapag natanggap ng MenuItem ang isang event ng klik.