# Virtual Flight Engineer - Checklist Automation for MSFS 2024

**Version 3.0.1, July 31, 2026**

**VirtualFE** is a Python-based external client application and VS2022 C++ wasm bridge module for **MSFS 2024** 
which automates checklists in native and addon aircraft in MSFS.


See **[tutorial videos](https://www.youtube.com/playlist?list=PLSkQkNS9pCjA)** providing checklist development and test process and completed checklist operation.

**Background**
- Version 1 introduced flight plan load for the CIVA INS in DC Designs Concorde using mouse-macro automation. 
- Version 2 uses Simconnect and a `WASM bridge` module to load the flight plan.
- Phased flight plan load with INS switch and dial setting and custom coordinate formatting. 
- Flight plan tracking using telemetry warns of pending new load.
- Version 3 extends the Verison 2 architecture to provide generic checklist or single control automation for native MSFS aircraft and addons.

## ✈️ Version 3 Features

- Application architecture components:
    - Client application executable 
    - Simconnect MSFS communication layer
    - VFEtray.exe system tray app supported version 1 mouse-macro automation, flight plan dialogue display. Retained for future versions to also allow client app show and hide.
    - WASM bridge module providing var scanning and RPN simple and compound string execute
- Panel, checklist, variable and action data tied to an aircraft
- Hotkey capture from game controllers and keyboard assigned to current checklist
- Auto scan of `Lvars` and `Simvars` and load of panels and checklists on aircraft detection
- Checkable UI sections collapse for a small footprint during development or flight. The VFE app may be minimised with global hotkeys available in flight.
- Support for H: events and B: events through VFE's wasm bridge
- Custom inline messages, pauses
- Messages may be:
    - text only in a box shown in the top left corner of the MSFS window; 
    - voice and text using the standard Windows `Speech` and `Voice` support; 
    - Voice support only
- Convenient lists for variable and action picking
- Custom RPN popout edit dialogue for easier compund RPN editing
- Standard reference switch, dial, rotary, button and position support
- Dynamic `Switch Show` as switch support is added to a checklist, moves the switch and restores to original position.
- A `Test Current Checklist` button which will run the checklist with a message box inserted before each step to allow confirmation of sequence and function.
- Custom RPN support including complex strings with embedded L:, B: and H: vars
- Sharable aircraft profiles through `backup` and `restore` buttons
- `View JSON` button displays the complete aircraft profile content.
- Version 3.0 has been tested with the Asobo C172SP, Black Square TBM 850 and DC Designs Concorde to confirm native and addon MSFS 2024, and 2020-ported aircraft use.
- Some C172SP pre-fight checklists packaged in the release


 

## ⚠️ Notes and Warnings
  
1.  Target Focus: Output is targeted specifically at the MSFS process. If MSFS is not running the `system status` will change and automation operations suspended. Whilst Simconnect use does not require window focus, inline messaging during the checklist does. 

2. VirtualFE.exe runs "on top" of other applications to facilitate checklist definition, but may be minimised during flight.
    
6. The project is released in executable format. Source is available in Github with an MIT license

3. The MSFS checklist environment is not accessible through APIs. All markeplace aircraft have encrypted asset files. Addon aircraft purchased externally may have accessible XML files for checklists to allow item names to be copy-pasted into VFE. 

4. Checklist development requires use of the MSFS developer, `Behaviours` mode to identify event, var and RPN expressions for use in the checklist. In some aircraft, documentation or intuitive var naming can bypass this step.

4. B: vars can be executed through rpn strings but in the current version 3.0 these types are not scanned for current values.

5. The application detects the first aircraft load, but must be restarted for aircraft change in MSFS.

## Development

This project was developed through a collaborative process between the author and Google Gemini. 
- Role: Gemini assisted in advising on specific architectures for IPC, system tray app methods, developing specific functions, and optimizing logic.
- Oversight: All AI-generated code was manually reviewed and tested to ensure it meets project needs.


## Terminology
    

## 🛠️ Requirements

- Local MSFS 2024 Installation
- Controllers or keyboard for `hotkey` assignment


## 🚀 Installation & Setup

1. **Download** this release zip file and extract to an application folder of your choice.

2. **Dependencies** The release package is self-contained.
   
4. **Copy** the `vfe-bridge-module` folder to your MSFS 2024 community folder. 

5. **Optionally** 
    - Launch the `VirtualFE.exe` once which will create the `Appdata\Roaming\msfsVFE` folder. From the application `templates` folder copy the **aircraft_panels_C172SP_G1000_Passengers_backup.json** file and paste to `msfsVFE`.
    - Edit the simvar_filter.json file to allow or remove variables from the reference var list box in VFE, The default file contains entries unrelated to cockpit use. The strings will filter by a partial match on the simvar name. eg Remove all ATC variables by adding "ATC" to the list
    ```
    [
    "interactive ",
    "ORNITHOPTER",
    "MARSHALLER",
    "LIQUID DROPPING",
    "LIGHT AMBIENT",
    "JETWAY ", ...
    ```

6. Launch MSFS and once started and aircraft selected, launch `VirtualFE.exe`

	
## 📁 Project Folder Structure

**Client Application Folder**
```    
virtualFE_app_folder/
├── README.md
├── vfe_systray.exe
├── VirtualFE.exe
├── VirtualFE.log               [logger file]
├── VirtualFE_output.log        [stdout file]
├── VirtualFE_errors.log        [stderr file]
├── templates/
│   ├── aircraft_panels_C172SP_G1000_Passengers_backup.json
│   ├── aircraft_panels_DCDesigns_Concorde_backup.json
│   ├── simvars.json
│   └── simvar_filter.json
├── vfe-bridge-module/
│   ├── layout.json
│   ├── manifest.json
│   └── Modules/
│       ├── VFE-bridge-module.wasm
│       └── wasm.xml
└──  videos/
     └── Numbered 1-8 checklist development and test videos

```

**.. APPDATA \ Roaming \ msfsVFE Folder**

```    
msfsVFE/
├── settings.json           [application presistent settings]
├── aircraft_panels.json    [all aircraft framework data]
├── engine_debug.log        [VFE_tray.exe log file]
└── aircraft_panels_{aircraft name}.json
```
    
    
## 🚀 Roadmap
- [X] Extend to handle generic checklist named panel automation.
- [ ] Add more usage videos
- [ ] Develop templates for additional aircraft
- [ ] Support aircraft change without restart
- [ ] Popout dialogues for var and action lists
- [ ] Scan B: vars on startup
- [ ] Non-marketplace aircraft checklist XML scan and optional load of name and item names


## ⚖️ License

This project is licensed under the MIT License.


