# NrMode Switcher

**Select NSA / SA mode for 5G using oplus radio service**

## Supported modes

- Auto (Placeholder, check below)  
- NSA Preferred (0)  
- NSA Only (1)  
- SA Only (2)  
- SA Preferred (3)

## About Auto mode

Stock rom chooses best mode based on location and signal strength, which won't be implemented in custom roms.  
As a result, auto mode here is just a placeholder for users who want to restore their preferences.  
By default, auto mode points to SA Preferred (3). You can change this by adding prop in your device tree
```
persist.sys.radio.nrmode.auto=X
```
(Change X to accroding number of the mode you want to set)

## How to build into rom

- Clone this repo into `ROM_SOURCE_PATH/packages/apps`
- Add this into any makefile of your device tree
```
# NrModeSwitcher
PRODUCT_PACKAGES += \
    NrModeSwitcher
```
- Pick sepolicy rules from https://github.com/Nameless-AOSP-OSS/hardware_oplus/commit/6f5e84952048c43cc1ac3a0ccd6259df63aaded9

## How to launch

There's no icon on launcher by design.

Launch it with
`adb shell am start org.nameless.nrmode/org.nameless.nrmode.NrModeSettingsActivity`

You can also integrate into Settings or device parts

```
<Preference
    android:key="nr_mode_switcher"
    android:persistent="false"
    android:title="@string/nr_mode_switcher_title"
    android:summary="@string/nr_mode_switcher_summary">
    <intent
        android:targetPackage="org.nameless.nrmode"
        android:targetClass="org.nameless.nrmode.NrModeSettingsActivity" />
</Preference>
```
