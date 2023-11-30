## 0.1.28

**Important**: Add a new cover entity (cover2) for D2-05-00. This should fix inverted position issue (thanks to @didi31).

### Fixed
- Add a new cover entity (cover2) for D2-05-00. This should fix inverted position issue (thanks to @didi31).   
  See mak-gitdev/HA_enoceanmqtt#94 for more details.

### Added
- Add support for:
   - D2-14-30 (Netsecur smoke detector with temperature and humidity sensors)
   - F6-04-01. **All NodOn devices to date are now supported.**
   - D2-50-00 (thanks to @billeranton for testing and initial mapping)
   - D2-50-01
   - D2-50-10
   - D2-50-11
   - A5-20-01 (control+status)
   - A5-20-04 (control+status)
   - A5-20-06 (control+status, thanks to @stefanhofmann2)
   - A5-14-09 (thanks to @juame)
   - A5-13-04
   - A5-13-05
   - A5-13-06
- Add switches for F6-02-01/02 virtual entities in addition to the existing select entities.

### Changed
- Add A5-13-04, A5-13-05 and A5-13-06 entities to A5-13-01 as requested by the EEP specification.

### Removed
None

## 0.1.27

### Fixed
- Fixes device selection error (see mak-gitdev/HA_enoceanmqtt#73 and embyt/enocean-mqtt#43 for more details)
- Fix issue mak-gitdev/HA_enoceanmqtt#77 related to MQTT entity naming
- Fix issue mak-gitdev/HA_enoceanmqtt#72

### Added
- Add support for:
   - D2-01-01
   - D2-01-09
   - A5-09-04
   - A5-30-03
   - A5-30-04
   - A5-38-08 (Command 2)
- Added new configuration entry `use_dev_name_in_entity` to select whether to use device name in the name of entities.   
   This is for users of HA versions from 2023.8.1 to the one before 2024.2.0.   
   For users of version before 2023.8.1, this entry is internally forced to true.   
   For users of version starting from 2024.2.0, this will be internally forced to false.   

### Changed
None

### Removed
None

## 0.1.26

### Fixed
- Use latest enocean-mqtt version which fixes status bits setting (see mak-gitdev/HA_enoceanmqtt#65 and embyt/enocean-mqtt#41 for more details)
- From now, use mak-gitdev/enocean as Python EnOcean Library which fixes "list index out of range error" thanks to @kridgo patch (see kipe/enocean#134 and kipe/enocean#138 for more details).

### Added
- Add virtual A5-10-06 (mak-gitdev/HA_enoceanmqtt#46)
- Add '%' as unit of measurement for A5-20-01 current value field (mak-gitdev/HA_enoceanmqtt#53)
- Update F6-02-[01-02] to send status bits

### Changed
None

### Removed
None

## 0.1.25

### Fixed
- Fix issue mak-gitdev/HA_enoceanmqtt#41

## 0.1.24

**Important**: Change devices and entities unique ids. This may lead to some devices loosing some configurations such as zones, etc.

### Fixed
- Fixed issue mak-gitdev/HA_enoceanmqtt#37

## Added
- Add support for virtual devices. We can now declare more than one device sending broadcast data. Only F6-02-01 and F6-02-02 are available at the moment.
- Add EEP documentation for each device.
- Add packet receipt date to all devices so that it is possible to know the last time the device has been seen.
- Add support for:
  - D2-01-0A
  - D2-01-0D
  - D2-01-0E
  - A5-13-[01-06]
  - A5-10-03
  - A5-10-05
  - A5-10-06
  - A5-10-10
  - A5-10-12
  - A5-08-[01-03]
  - A5-14-01
  - A5-14-0A
  - A5-20-01 (no control yet, only status)
  - A5-20-04 (no control yet, only status)
  - Initial support for A5-38-08 command 1
- Add measurement control entities for D2-01-0B, D2-01-0C and D2-01-0E.
- Add a new configuration entry `eep_file` to add support for new EEPs at Python EnOcean library level.

### Changed
- Change devices and entities unique ids. This may lead to some devices loosing some configurations such as zones, etc.
- Add better support for A5-13-01. ID1, ID2 and ID3 are now supported. ID4 to ID6 will follow in another release.
- Use device triggers for D2-03-0A instead of binary sensors.

### Removed
- Remove some unused entities from D2-01-xx devices to comply with the EEP documentation.
- Remove delete entity from devices. Devices can now be deleted using the integrated MQTT delete button.

## 0.1.23

**Note**: Rename versions in changelog

### Fixed
- Fix issue mak-gitdev/HA_enoceanmqtt#27
- Fix status entity for A5-04-XX devices.

### Added
- Add support for:
  - A5-02-[01-0B]
  - A5-02-[10-1B]
  - A5-02-20
  - A5-02-30
  - A5-06-[01-02]
  - A5-07-[01-03]
  - A5-13-01
  - D2-03-0A

### Changed
- Rename not rounded entities `xx_temperature` and `xx_humidity` from A5-04-XX devices to `t_raw` and
  `h_raw`. These new entities are also disable by default.

### Removed
- Remove °F entities from A5-04-XX devices as HA seems to convert automatically °C to °F and vice-versa

## 0.1.22 (previously `dev` in addon and `20221125-1` in changelog)
First version of addon-dev to track the develop branch

### Added
- Add support for A5-04-[01-04] devices

### Fixed
- Fix issue #10
