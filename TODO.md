# Android Emulator Fix - TODO List

## ✅ Completed Steps
- [x] Created `.vscode/settings.json` with correct Android SDK paths
- [x] Created `.vscode/launch.json` with emulator launch configurations

## 🔄 Next Steps to Complete

### 1. Set Environment Variables (Required)
You need to set the Android SDK environment variables in Windows:

**Option A: Via System Settings (Recommended)**
1. Press `Win + R`, type `sysdm.cpl` and press Enter
2. Go to "Advanced" tab → "Environment Variables"
3. Add these **User variables**:
   - `ANDROID_HOME` = `C:\Users\smaka\AppData\Local\Android\sdk`
   - `ANDROID_SDK_ROOT` = `C:\Users\smaka\AppData\Local\Android\sdk`
4. Edit `Path` variable and add:
   - `%ANDROID_HOME%\emulator`
   - `%ANDROID_HOME%\platform-tools`
   - `%ANDROID_HOME%\tools`

**Option B: Via PowerShell (Temporary)**
```powershell
$env:ANDROID_HOME = "C:\Users\smaka\AppData\Local\Android\sdk"
$env:ANDROID_SDK_ROOT = "C:\Users\smaka\AppData\Local\Android\sdk"
```

### 2. Verify Android SDK Installation
Run these commands in PowerShell to verify:
```powershell
# Check if emulator command works
C:\Users\smaka\AppData\Local\Android\sdk\emulator\emulator.exe -list-avds

# Check if adb works
C:\Users\smaka\AppData\Local\Android\sdk\platform-tools\adb.exe devices
```

### 3. Restart VS Code
- Close VS Code completely
- Reopen it from the project directory
- Try `Ctrl+Shift+P` → "Flutter: Launch Emulator" again

### 4. Alternative: Use Command Line
If VS Code still doesn't work, you can launch emulators from command line:
```powershell
# List available emulators
C:\Users\smaka\AppData\Local\Android\sdk\emulator\emulator.exe -list-avds

# Launch a specific emulator (replace <emulator_name>)
C:\Users\smaka\AppData\Local\Android\sdk\emulator\emulator.exe -avd <emulator_name>
```

## 📝 Notes
- The error showing `~\Library\Android\sdk` is a default fallback path used by the Flutter extension when it can't find the Windows SDK path
- The configuration files I created will help VS Code find the correct Windows paths
- Make sure you have at least one Android Virtual Device (AVD) created in Android Studio
