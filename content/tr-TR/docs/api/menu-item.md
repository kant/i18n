## Sınıf: MenuItem

> Yerel uygulama menülerine ve bağlam menülerine öğeler ekleyin.

İşlem: [Ana](../glossary.md#main-process)

[`Menu`](menu.md) örnekleri için bkz.

### `new MenuItem(options)`

* `seçenekler` Nesne 
  * `click` Function (isteğe bağlı) - menuye basıldığı zaman `fonksiyon click(menuItem, browserWindow, event) ile birlikte` çağırılmış olacak. 
    * `menuItem` MenüÖğesi
    * `browserWindow` [BrowserWindow](browser-window.md)
    * `event` Olay
  * `role` String (optional) - Can be `undo`, `redo`, `cut`, `copy`, `paste`, `pasteandmatchstyle`, `delete`, `selectall`, `reload`, `forcereload`, `toggledevtools`, `resetzoom`, `zoomin`, `zoomout`, `togglefullscreen`, `window`, `minimize`, `close`, `help`, `about`, `services`, `hide`, `hideothers`, `unhide`, `quit`, `startspeaking`, `stopspeaking`, `close`, `minimize`, `zoom` or `front` - Define the action of the menu item, when specified the `click` property will be ignored. See [roles](#roles).
  * `type` String (isteğe bağlı) - `normal`, `separator`, `submenu`, `checkbox` veya `radio` olabilir.
  * `label` String (optional)
  * `sublabel` String (optional)
  * `accelerator` [Accelerator](accelerator.md) (isteğe bağlı)
  * `icon` ([NativeImage](native-image.md) | String) (isteğe bağlı)
  * `enabled` Boolean (isteğe bağlı) - Eğer değer false ise, menü öğesi soluk ve tıklanamaz olacaktır.
  * `visible` Boolean (optional) - Eğer değer false ise, menü öğesi tamamen görünmez olacaktır.
  * `checked` Boolean (isteğe bağlı) - Yalnızca `checkbox` veya `radio` türü menü öğeleri için belirtilmiş olmalıdır.
  * `registerAccelerator` Boolean (optional) - If false, the accelerator won't be registered with the system, but it will still be displayed. Defaults to true.
  * `submenu` (MenuItemConstructorOptions[] | [Menu](menu.md)) (optional) - Should be specified for `submenu` type menu items. If `submenu` is specified, the `type: 'submenu'` can be omitted. If the value is not a [`Menu`](menu.md) then it will be automatically converted to one using `Menu.buildFromTemplate`.
  * `id` String (isteğe bağlı) - Tek bir menu içinde benzersiz. Eğer tanımlanmışsa o zaman öğe pozisyon özelliğiyle bu öğeye referans gibi kullanılabilir.
  * `before` String[] (optional) - Inserts this item before the item with the specified label. If the referenced item doesn't exist the item will be inserted at the end of the menu. Also implies that the menu item in question should be placed in the same “group” as the item.
  * `after` String[] (optional) - Inserts this item after the item with the specified label. If the referenced item doesn't exist the item will be inserted at the end of the menu.
  * `beforeGroupContaining` String[] (optional) - Provides a means for a single context menu to declare the placement of their containing group before the containing group of the item with the specified label.
  * `afterGroupContaining` String[] (optional) - Provides a means for a single context menu to declare the placement of their containing group after the containing group of the item with the specified label.

### Roller

Roller, menü öğelerinin önceden tanımlanmış davranışlara sahip olmalarını sağlar.

Bir `click` fonksiyonu içinde davranışını el ile uygulamaya çalışmaktansa standart rolle eşleşen herhangi bir menü öğesi için `role` belirtmek en iyisidir. Yerleşik `role` davranışı en iyi doğal deneyimini verecektir.

`label` ve `accelerator` değerleri bir `rol` kullanırken isteğe bağlıdır ve her platform için uygun değerleri varsayılan olur.

Every menu item must have either a `role`, `label`, or in the case of a separator a `type`.

`role` özelliği aşağıdaki değerlere sahiptir:

* `geri almak`
* `yeniden yapmak`
* `kes`
* `kopyala`
* `paste`
* `pasteAndMatchStyle`
* `selectAll`
* `sil`
* ` minimize ` - Geçerli pencereyi simge durumuna küçültme.
* `close` - Geçerli pencereyi kapatma.
* `quit` - Quit the application.
* `reload` - Geçerli pencereyi yeniden yükleme.
* `forceReload` - Reload the current window ignoring the cache.
* `toggleDevTools` - Toggle developer tools in the current window.
* `toggleFullScreen` - Toggle full screen mode on the current window.
* `resetZoom` - Reset the focused page's zoom level to the original size.
* `zoomIn` - Zoom in the focused page by 10%.
* `zoomOut` - Zoom out the focused page by 10%.
* `fileMenu` - Whole default "File" menu (Close / Quit)
* `editMenu` - Tüm varsayılan "Düzenle" menüsü (Geri alma, Kopyalama, vb.).
* `viewMenu` - Whole default "View" menu (Reload, Toggle Developer Tools, etc.)
* `windowMenu` - Whole default "Window" menu (Minimize, Zoom, etc.).

The following additional roles are available on *macOS*:

* `appMenu` - Whole default "App" menu (About, Services, etc.)
* `about` - `orderFrontStandardAboutPanel` eylemine eşleme.
* `hide` - `hide` eylemine eşleme.
* `hideOthers` - Map to the `hideOtherApplications` action.
* `unhide` - `unhideAllApplications` eylemine eşleme.
* `startSpeaking` - Map to the `startSpeaking` action.
* `stopSpeaking` - Map to the `stopSpeaking` action.
* `front` - `arrangeInFront` eylemine eşleme.
* `zoom` - `performZoom` eylemine eşleme.
* `toggleTabBar` - Map to the `toggleTabBar` action.
* `selectNextTab` - Map to the `selectNextTab` action.
* `selectPreviousTab` - Map to the `selectPreviousTab` action.
* `mergeAllWindows` - Map to the `mergeAllWindows` action.
* `moveTabToNewWindow` - Map to the `moveTabToNewWindow` action.
* ` window ` - Alt menü bir "Pencere" menüsüdür.
* `help` - Alt menü bir "Yardım" menüsüdür.
* `services` - The submenu is a ["Services"](https://developer.apple.com/documentation/appkit/nsapplication/1428608-servicesmenu?language=objc) menu. This is only intended for use in the Application Menu and is *not* the same as the "Services" submenu used in context menus in macOS apps, which is not implemented in Electron.
* `recentDocuments` - The submenu is an "Open Recent" menu.
* `clearRecentDocuments` - Map to the `clearRecentDocuments` action.

When specifying a `role` on macOS, `label` and `accelerator` are the only options that will affect the menu item. All other options will be ignored. Lowercase `role`, e.g. `toggledevtools`, is still supported.

**Nota Bene:** The `enabled` and `visibility` properties are not available for top-level menu items in the tray on MacOS.

### Örnek Özellikleri

Aşağıdaki özellikler `MenuItem` örneklerinde mevcuttur:

#### `menuItem.enabled`

Öğenin etkin olup olmadığını gösteren bir `Boolean` vardır, bu özellik dinamik olarak değiştirilebilir.

#### `menuItem.visible`

Öğenin görünür olup olmadığını gösteren bir `Boolean` vardır, bu özellik dinamik olarak değiştirilebilir.

#### `menuItem.checked`

Öğenin işaretli olup olmadığını gösteren bir `Boolean` vardır, bu özellik dinamik olarak değiştirilebilir.

Bir `checkbox` menü öğesi seçildiğinde `checked` özelliği etkinleştirip devre dışı bırakacaktır.

Bir `radio` menü öğesi tıklandığında `checked` özelliğini açar ve bu özelliğin aynı menüdeki tüm bitişik öğeler için kapatılmasına neden olur.

Ek davranış için bir `click` işlevi ekleyebilirsiniz.

#### `menuItem.label`

Görünen menü öğelerini bir `String` temsil eder.

#### `menuItem.click`

MenuItem bir tıklama olayı aldığında tetiklenen bir `Function`'dır.