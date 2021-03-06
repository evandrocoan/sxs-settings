# Side-by-Side Settings

A Sublime Text plugin for viewing default and user settings side by side in a
new window. It also works for key bindings and plug-in specific settings, making
it much easier to configure Sublime Text.


## Installation

### By Package Control

1. Download & Install **`Sublime Text 3`** (https://www.sublimetext.com/3)
1. Go to the menu **`Tools -> Install Package Control`**, then,
    wait few seconds until the installation finishes up
1. Now,
    Go to the menu **`Preferences -> Package Control`**
1. Type **`Add Channel`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    input the following address and press <kbd>Enter</kbd>
    ```
    https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
    ```
1. Go to the menu **`Tools -> Command Palette...
    (Ctrl+Shift+P)`**
1. Type **`Preferences:
    Package Control Settings – User`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    find the following setting on your **`Package Control.sublime-settings`** file:
    ```js
    "channels":
    [
        "https://packagecontrol.io/channel_v3.json",
        "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
    ],
    ```
1. And,
    change it to the following, i.e.,
    put the **`https://raw.githubusercontent...`** line as first:
    ```js
    "channels":
    [
        "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
        "https://packagecontrol.io/channel_v3.json",
    ],
    ```
    * The **`https://raw.githubusercontent...`** line must to be added before the **`https://packagecontrol.io...`** one, otherwise,
      you will not install this forked version of the package,
      but the original available on the Package Control default channel **`https://packagecontrol.io...`**
1. Now,
    go to the menu **`Preferences -> Package Control`**
1. Type **`Install Package`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    search for **`SideBySideSettings`** and press <kbd>Enter</kbd>

See also:

1. [ITE - Integrated Toolset Environment](https://github.com/evandrocoan/ITE)
1. [Package control docs](https://packagecontrol.io/docs/usage) for details.


## Usage

`{ "keys": ["ctrl+k", "ctrl+s"], "command": "sxs_settings" }`

Side-by-Side Settings adds three new commands to the command palette:

* **Side-by-Side: Select a File** - Opens a panel displaying all of the `.sublime-settings` and `.sublime-keymap` files in the Sublime Text environment
* **Side-by-Side: Sublime Settings** - Opens both default and user Sublime Text settings side by side in a new window
* **Side-by-Side: Sublime Key Bindings** - Opens both default and user Sublime Text key bindings side by side in a new window

#### Select a File Command

The "select a file" command opens a quick panel that displays all of the
`.sublime-settings` and `.sublime-keymap` files that Sublime Text knows about
(note that files located in the `Packages/User` directory are filtered out of
this list; more on why it does this in a second). When a file in the quick panel
is selected, it becomes the "left" panel in the comparison window. The "right"
panel will contain the corresponding user settings file, typically located in
the `Packages/User` directory (hence why files in `User` are filtered out).

Side-by-Side Settings tries to do the correct thing depending on the file you
select in the quick panel. If the file you select is a platform-specific
settings file (e.g. `Default/Preferences (Windows).sublime-settings`), the
corresponding user file that gets opened will be `Preferences.sublime-settings`
(in the `Packages/User` directory). This is due to the fact that platform-
specific files in the `User` directory are ignored by Sublime Text. Likewise, if
you select any `.sublime-keymap` file, the appropriate platform-specific
`.sublime-keymap` file in the `User` directory will be opened.

#### Default Keyboard Shortcut

By default, the key-chord `Ctrl+K, Ctrl+S` is bound to the "select a file"
command. If you wish to bind any of the commands to a different key, here are
the internal command names to use:

* sxs_select_file
* sxs_settings
* sxs_key_bindings

Here's an example key binding:

`{ "keys": ["ctrl+k", "ctrl+s"], "command": "sxs_settings" }`

## Plug-in Settings

Side-by-Side Settings currently supports the following plug-in specific
settings:

**filter_platform**: When enabled, platform specific files that do not match
your current platform are filtered out of the files shown in the file selection
panel. Defaults to true.

**hide_minimap**: Specifies whether the minimap should be displayed or not when
opening a side-by-side session. Defaults to false.

**open_in_distraction_free**: This option allows the side-by-side window to open
in distraction free mode, essentially resulting in a full-screen window. This
option defaults to false.

## Reporting Bugs & Suggesting Features
If you spot a bug in this plug-in, or you have a feature request, please open an
issue over on the [issues page](https://github.com/jgbishop/sxs-settings/issues)
at GitHub.

## License
See the `LICENSE` file under this repository.


## Acknowledgements
My thanks to the following folks:

* Jeremy Bolding for providing several plug-in suggestions.
* Ben Felder for suggesting the filter_platform option.
