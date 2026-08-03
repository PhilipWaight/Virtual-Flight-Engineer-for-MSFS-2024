# Virtual Flight Engineer - Changelog

All notable changes to this project will be documented in this file.


## V3.0.2 - 2026-08-03

### Added
- AviationTextNormalizer class to expand shorthand labels into complete words for clear voice synthesis
- Built a starting aviation text list from simvar definitions
- Synchronised (scroll and select) `actions list` item, `actions reference` item and `scanned var` item from selected `ordered var`
- Complete Pre-flight, before start and COld start on battery checklists, including prompting pilot for actions.

### Changed

### Fixed
- `Custom Action Field` decimal value entry was treating '.' as a delimiter
- Prepended `CUSTOM.. | ` and `ACTION.. |` in the `Custom Action Value` field as happens with a paste of an assigned value for editing, was not trimmed as a duplicate

