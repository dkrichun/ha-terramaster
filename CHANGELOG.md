# Changelog

All notable changes to this project will be documented in this file.

The format is based on Keep a Changelog.

---

## [1.2.1] - 2026-11-27

### Added
- Per-disk total data read/written sensors computed from SMART: SATA attributes 241/242 (Total LBAs Written/Read) and NVMe "Data Units Read/Written", exposed in gigabytes. Power-on time is shown in days.

### Tests
- SATA LBA totals and NVMe data units parsing.

## [1.2.0] - 2026-11-27

### Changed
- Privileged collection (SMART, shared folders, TOS version) now tries a direct run first and falls back to `sudo`. On TOS 7 the shell user can access SMART data directly, while `sudo` restricts device access; older TOS versions continue to use `sudo`. The working mode is cached per client.

### Added
- NVMe disk discovery and monitoring: SMART health, temperature, power-on hours and power cycles via the controller's first namespace.
- Additional TOS version file locations for newer TOS releases.

### Tests
- Direct-first privileged collection, sudo fallback, unavailable mode and NVMe SMART parsing.

## [1.1.6] - 2026-11-04

### Fixed
- Replace the remaining deprecated `async_get_device()` call in the shared-folder view with config-entry-scoped `async_get_device_by_identifier()` for Home Assistant 2027.8.0 compatibility.

### Changed
- Lead with default-catalog HACS installation instructions and retain the custom-repository method as an alternative.

### Tests
- Verify shared-folder navigation uses the config-entry-scoped device lookup and does not call the deprecated API.

## [1.1.5] - 2026-11-03

### Fixed
- Discover TerraMaster sensors through the Home Assistant entity registry, including translated entity IDs.
- Resolve dashboard metrics from stable entity unique IDs and scope discovery to one NAS.
- Request native full-section width in Home Assistant Sections dashboards while retaining Panel view support.
- Format numeric sensor values to two decimal places and convert large GB readings to TB for a more compact dashboard.
- Show NAS uptime and disk operating durations in human-readable days, hours and minutes.

### Tests
- Cover translated entity IDs, NAS isolation, native Sections grid options, numeric formatting and durations.

## [1.1.4] - 2026-11-03

### Fixed
- Replace deprecated device registry lookup with the config-entry-scoped `async_get_device_by_identifier` API for compatibility with Home Assistant 2027.8.0 and later.

## [1.1.3] - 2026-11-03

### Added
- Bundle an experimental Lovelace NAS dashboard with CPU, memory, temperature, storage and system summary tiles.
