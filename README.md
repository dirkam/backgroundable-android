# Backgroundable Android
Collection of stock apps and mechanisms from various manufacturers, which might affect background tasks and scheduled alarms with AlarmManager, etc., or apps in background in general. Also focusing on those, which prevent 3rd party apps from auto start after device boot.

## Why?
Most of modern Android devices come with an app or mechanism, which automagically tries to figure out how to save battery and as a result might kill certain 3rd party apps. This might result in removing scheduled tasks and jobs, (e.g. alarms not going off, push notification not working, etc.). In many cases this happens completely independent from battery saving mechanisms of Android (such as Doze, which can be controlled correctly).

## How?
Though battery saving is important and 3rd party apps should be designed with this in mind, if the basic function of an app requires it to be kept running in the background then there should be a way to add it to exception lists. Unfortunately, in most cases, this is not possible from within the app itself. However, in many cases, there are white lists where users can manually add certain 3rd party apps.
This list is a repository of known battery saving apps and mechanisms along with an Intent (or at least a Step-by-step guide), which can be started/shown to navigate the user to the relevant settings menu directly.

## How to contribute?
Open an issue or pull request if you found something wrong or have a new one to add. Please try to follow the following structure:

### Name of the app or mechanism

**Manufacturer:** Name of the manufacturer.

**Build.MANUFACTURER:** Sometimes the device returns a completely different manufacturer name from what one would expect.

**Build.MODEL:** Sometimes it is only related to certain devices (or not related to certain devices).

**Known restrictions:** If there is any known restriction (e.g. SDK version)

**Steps:** Step-by-step guide how one can find it in on the device.

**Intents:** Intents that can be started from the app to navigate the user directly to the settings.

*Information below or in any other part of this repository might be incorrect or not 100% accurate. Always try to double check it and use at your own risk.*

## What's known

### Samsung Unmonitored Apps (7.0+)
**Manufacturer:** Samsung

**Build.MANUFACTURER:** samsung

**Build.MODEL:** Applies to all

**Known restrictions:** Android 7.0+ only

**Steps:**
1. Settings
2. Device maintenance
3. Battery
4. Unmonitored apps list

**Intents:**

```java
new Intent().setComponent(new ComponentName("com.samsung.android.lool",
                        "com.samsung.android.sm.ui.battery.BatteryActivity"))
```

### Huawei Protected Apps (older EMUI)
**Manufacturer:** Huawei

**Build.MANUFACTURER:** huawei

**Build.MODEL:** NOT nexus

**Known restrictions:** Not applies to Huawei Nexus devices (which run stock Android). Up to Android 7.

**Steps:**
1. Settings
2. Advanced Settings
3. Battery Manager
4. Protected Apps

or

1. Settings
2. Privacy and Security
3. Protected Apps

**Intents:**

```java
new Intent().setComponent(new ComponentName("com.huawei.systemmanager",
                        "com.huawei.systemmanager.optimize.process.ProtectActivity"))
```

### Huawei Phone manager (newer EMUI) NEEDS VERIFICATION
**Manufacturer:** Huawei

**Build.MANUFACTURER:** huawei

**Build.MODEL:** NOT nexus

**Known restrictions:** Not applies to Huawei Nexus devices (which run stock Android). From Android 7.

**Steps:**
1. Phone Manager
2. Battery
3. Lock screen cleanup
4. Set to 'Don't close' (unchecked)

or

1. Settings
2. Apps
3. App name
4. Enable App Auto-Launch
5. Enable Keep running after screen off

**Intents:**

```java
//TODO
```


### Sony STAMINA
**Manufacturer:** Sony

**Build.MANUFACTURER:** sony

**Build.MODEL:** Applies to all

**Known restrictions:** Some old Android (4.something) versions don't have this feature.

**Steps:**
1. Settings
2. Power management
3. STAMINA mode
4. Apps active in standby

**Intents:**

```java
//TODO
```

### Xiaomi Auto Start and Battery usage monitoring
**Manufacturer:** Xiaomi

**Build.MANUFACTURER:** xiaomi

**Build.MODEL:** Applies to all (running MIUI)

**Known restrictions:** Applies to devices running MIUI (not the ones with Android One)

**Steps:**
1. Settings
2. Additional Settings
3. Battery & Performance
4. Manage Apps Battery Usage
5. Choose Apps
6. No restrictions

and

1. Settings
2. Permissions
3. Auto-run management

**Intents:**

```java
new Intent("miui.intent.action.POWER_HIDE_MODE_APP_LIST").addCategory(Intent.CATEGORY_DEFAULT)
new Intent("miui.intent.action.OP_AUTO_START").addCategory(Intent.CATEGORY_DEFAULT)
```

### Elephone background task clearer
**Manufacturer:** Elephone

**Build.MANUFACTURER:** elephone

**Build.MODEL:** Applies to all

**Known restrictions:** Not known

**Steps:**
1. Settings
2. Background task clear
3. White list

**Intents:**

```java
//TODO
```

### ASUS auto start
**Manufacturer:** ASUS

**Build.MANUFACTURER:** asus

**Build.MODEL:** Applies to all

**Known restrictions:** Asus mobile manager app installed

**Steps:**
1. Asus Mobile Manager
2. Auto-start Manager

**Intents:**

```java
getPackageManager().getLaunchIntentForPackage("com.asus.mobilemanager")
```


### OPPO auto start NEEDS VERIFICATION
**Manufacturer:** OPPO

**Build.MANUFACTURER:** oppo

**Build.MODEL:** Applies to all

**Known restrictions:** ColorOS 3.2

**Steps:**
1. Phone Manager
2. Privacy Permissions
3. Startup Manager

**Intents:**

```java
//TODO
```
