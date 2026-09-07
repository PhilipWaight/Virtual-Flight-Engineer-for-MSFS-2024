# Virtual Flight Engineer - Changelog

All notable changes to this project will be documented in this file.

## V3.2.0 - 2026-09-05

### Added

- **Menu Bar** and user interface improvements
    - `Status`, `Checklist`, `BuildView`, `Flight Plan` and `Settings` layouts
    - Simplified main checklist build view by moving settings and flight plan to other pages and telemetry to status and flight plan pages
    - Collapse to menu bar option for minimum footprint on MSFS
    - Improved settings page 
        - Settings saved to config\config.json 
        - Interface scale added
    - Progress log box replicated on multiple pages
    - Uses generic multi-view widget updater for status display, buttons status, panels and checklists
    
- Improved connection monitoring and aircraft change detection using telemetry

- 

## V3.1.0 - 2026-08-16

### Added
- Recommended Windows `volume mixer` settings for MSFS, VFE, to allow switch clicks to be heard
    - VirtualFE.exe 50% (source of voice)
    - MSFS.exe 100% (Settings:engines 30-50%; cockpit sounds-100%)
- MSFS var type support improved:
    - Clicking an `ordered var` item displays the var type in
    a header list.
    - Change the assigned var type with confirmation, for the rare situation where an aircraft type is mis-assigned, especially `A:simvar` with `L:var`.
    - A changed var type is made persistent by auto save to the aircraft config under `custom_var_map`
    - Context help button alongside var type list contains a definition of each var with usage notes.
- Inline message text `ACTION:MSG` supports basic `markdown` including `backtick` highlighting
- Checks for MSFS and Simconnect active before running checklists
- Adding new checklist provides option to add to all panels
    - A new empty checklist is added to each defined panel
    - Recommended procedure is to add all panels to current aircraft first followed by checklists which may be added to current or all panels
    - Hotkeys are defined against Panel and Checklist and must be defined for each instance required.
- `Show on top` application global setting added
- `Select Interface Scale` global setting added. Switches font between 10, 12 and 14 pt size
- `Voice announce checklist`  added to announce and complete the checklist. Replaces manual user message as a needed indicator that hotkey triggered checklist is running.
- `Shift-ESC` interrupt trigger added to VFE checklist support, consistent with flight plan interrupt

### Changed

- Ok button removed from ACTION:MSG dialogues. Display time of inline message is 10 secs or at the next msg request.
- Disabled UI during checklist operations
- UI layout minor changes to support UI scaling option
    - global settings now in grid
    - button text or icons more consistent

### Fixed

- `Float` action numeric overide now supported.
- Ordered var and action list boxes got out of alignment on dynamic display of horizontal scroll in either box. Fixed.
- INS flight plan load regression fixed.
- MSFS pop-out windows could be identified as the main window, affecting message displays. Fixed.
- Fixed a number of reported exceptions compiling checklists.



## V3.0.2 - 2026-08-05

### Added
- AviationTextNormalizer class to expand shorthand labels into complete words for clear voice synthesis
- Built a starting aviation text list from simvar definitions
- Synchronised (scroll and select) `actions list` item, `actions reference` item and `scanned var` item from selected `ordered var`
- Complete Pre-flight, before start and COld start on battery checklists, including prompting pilot for actions.
- Scanner var list items now copyable to alow paste directly to `Custom Action Value` field.

### Changed

### Fixed
- `Custom Action Field` decimal value entry was treating '.' as a delimiter
- Prepended `CUSTOM.. | ` and `ACTION.. |` in the `Custom Action Value` field as happens with a paste of an assigned value for editing, was not trimmed as a duplicate
- Fixed a regression in the CIVA INS flight plan load 
causing it to fail to load a flight plan.

