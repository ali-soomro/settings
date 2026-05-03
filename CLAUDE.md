# settings — Cutefish System Settings

## Purpose
System settings application covering appearance, display, fonts, cursor, network, VPN, Bluetooth, sound, power, datetime, touchpad, notifications, wallpaper, and more.

## Build
```bash
cmake -B build -DCMAKE_INSTALL_PREFIX=/usr && cmake --build build && sudo cmake --install build
```

## Dependencies
- Qt6 (Core, Gui, Widgets, Quick, QuickControls2, DBus, Xml, Concurrent, LinguistTools)
- X11, Freetype, Libcrypt
- KDE Frameworks 6 (KF6NetworkManagerQt, KF6ModemManagerQt, KF6Config)
- fontconfig (pkg-config), icu-i18n (pkg-config)

## Structure
- `src/application.cpp/h`, `src/main.cpp` — entry point
- `src/appearance.cpp/h`, `src/background.cpp/h`, `src/cicontheme.cpp/h` — theme/appearance
- `src/cscreenmanager.cpp/h`, `src/cscreenoutput.cpp/h` — display management
- `src/fontsmodel.cpp/h`, `src/fonts/kxftconfig.cpp`, `src/fonts/fonts.cpp` — font configuration
- `src/brightness.cpp/h`, `src/battery.cpp/h`, `src/batteryhistorymodel.cpp/h`, `src/powermanager.cpp/h` — power
- `src/language.cpp/h` — language settings
- `src/about.cpp/h` — about page
- `src/password.cpp/h` — password management
- `src/notifications.cpp/h` — notification settings
- `src/cursor/` — cursor theme model, mouse settings
- `src/datetime/` — time, timezone map, timedate D-Bus interface
- `src/touchpad.cpp/h` — touchpad settings
- `src/vpn/vpn.cpp/h` — VPN configuration
- `src/networkproxy.cpp/h` — network proxy
- `src/defaultapplications.cpp/h` — default apps
- `src/desktopproperties.cpp/h` — desktop properties
- `src/qml/` — 36 QML pages (About, Appearance, Battery, Bluetooth, Cursor, DateTime, Display, Dock, Fonts, Language, Notification, Power, Proxy, Sound, Touchpad, VPN, Wallpaper, Wired, WLAN, etc.)
- `src/com.cutefish.SettingsUI.xml` — D-Bus adaptor

## Install Targets
- Binary → `${CMAKE_INSTALL_BINDIR}`
- Desktop file `cutefish-settings.desktop` → `/usr/share/applications/`
- Translations → `/usr/share/cutefish-settings/translations/`

## Qt5→Qt6 Migration Notes
- Qt5 → Qt6, KF5 → KF6
- `QX11Info` → `QNativeInterface` helpers
- `QVariant` operator< removed — sort via `QStringList` instead

## Status
✅ Ported, built, installed, pushed (github.com/ali-soomro)
