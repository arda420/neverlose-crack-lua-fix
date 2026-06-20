# PulseFixer

PulseFixer is a simple Windows tool for fixing and bundling Neverlose Lua scripts with the required Lua libraries.

This package is meant to be used directly. You do not need Python, source code, or any build tools.

## Included Files

Make sure these files stay in the same folder:

```text
PulseFixer.exe
libs/
bundler_config.json
```

- `PulseFixer.exe` is the main application.
- `libs/` contains the Lua libraries used while fixing and bundling scripts.
- `bundler_config.json` stores saved profiles, paths, output names, and optional webhook settings.

## What PulseFixer Does

PulseFixer scans your main Lua file, finds supported `require(...)` calls, and tries to load the needed modules from the included `libs` folder. It then creates one bundled Lua file that contains the main script and the required libraries together.

This makes it easier to use scripts that normally depend on multiple external Lua files.

## How To Use

1. Open `PulseFixer.exe`.
2. Select a profile or create a new one.
3. Choose your main Lua script in `Main Lua File`.
4. Select the included `libs` folder in `Libs Folder`.
5. Enter an output file name, for example:

```text
fixed_script.lua
```

6. Click `BUILD BUNDLE`.

The fixed output Lua file will be created next to your selected main Lua script.

## Options

### Copy to Clipboard

When enabled, PulseFixer automatically copies the generated Lua code after a successful build.

### Upload to Discord

When enabled, PulseFixer uploads the generated Lua file to the Discord webhook saved in the profile.

Only use your own webhook. Do not share private webhook links with other people.

### Live Watcher

When enabled, PulseFixer watches your selected main Lua file and the `libs` folder. When you save a change, it automatically rebuilds the output file.

## Supported Require Examples

PulseFixer supports common Lua require formats like:

```lua
require("module_name")
require "module_name"
require("folder.module_name")
```

For example:

```lua
require("utils.color")
```

will be searched inside `libs/` as:

```text
utils/color.lua
```

If PulseFixer cannot find a module inside `libs/`, it leaves that require call unchanged.

## Important Notes

- Keep `PulseFixer.exe`, `libs/`, and `bundler_config.json` together.
- Do not rename or delete the `libs` folder.
- Use readable `.lua` files. Encrypted or compiled Lua files cannot be bundled.
- If you move the folder, open PulseFixer and check your saved paths again.
- If a Discord webhook is saved in `bundler_config.json`, keep that file private.

## Troubleshooting

### Main file not found

Check that the selected main Lua file still exists and that the saved profile path is correct.

### Library not found

Make sure `Libs Folder` points to the included `libs` folder.

### Output file is not created

Check that the main Lua file is valid, readable, and not compiled or encrypted.

### Discord upload does not work

Check that the webhook URL is valid, active, and starts with:

```text
https://discord.com/api/webhooks/
```

Also make sure your internet connection is working.

## Recommended Folder Layout

```text
PulseFixer/
|-- PulseFixer.exe
|-- bundler_config.json
`-- libs/
    |-- example_library.lua
    |-- another_library.lua
    `-- ...
```

## Summary

PulseFixer helps you turn a Neverlose Lua script and its required libraries into one ready-to-use bundled Lua file. Select your script, select the included `libs` folder, choose an output name, and build.
