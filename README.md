- [Repository Information](#org886bb6a)
  - [Description](#org30c6fbd)
- [Images](#org2dbc793)
- [Usage Instructions](#orgcabb0db)
  - [Arduino Serial Monitor](#org7bc0b25)
  - [Python](#org02e9623)
  - [Matlab](#orgdf850e3)
- [Build Instructions](#orgdfb3080)
- [Software](#orgc9742b9)
- [Firmware](#orgd99c6ec)
  - [BacklightController](#orgd7c3fe5)
    - [Library Information](#org6a7eb5e)
    - [API NAMES](#orgaf34bff)
    - [API GENERAL](#org665d9b4)
    - [Ancestors](#orgc6151b5)
    - [Clients](#org1a261ea)
    - [Devices](#org80cbebd)
    - [More Detailed Modular Device Information](#org5692dd0)
    - [Installation Instructions](#org913fa5d)
  - [DigitalController](#org62d9d64)
    - [Library Information](#org37d32f6)
    - [API NAMES](#orgc62fd8e)
    - [API GENERAL](#org7314b4f)
    - [Ancestors](#org4b9eb1f)
    - [Clients](#org6bcc961)
    - [Devices](#org7d3e0ce)
    - [More Detailed Modular Device Information](#orgb81ac3e)
    - [Installation Instructions](#org7f9e787)
  - [SleepAssayController](#org4159958)
    - [Library Information](#org82a005d)
    - [API NAMES](#orgded87b0)
    - [API GENERAL](#org0e111c4)
    - [Ancestors](#org0b1cb98)
    - [Clients](#org9789570)
    - [Devices](#org1b96a96)
    - [More Detailed Modular Device Information](#org0e5d6f4)
    - [Installation Instructions](#org38d34b3)
- [Hardware](#orgc75dbcc)
  - [backlight\_controller\_3x2](#org5e67c8e)
    - [Repository Information](#org00e12f0)
    - [Images](#orgae57cdb)
    - [Schematic](#org7bc1d0f)
    - [Gerbers](#orgcfdda6f)
    - [Bill of Materials](#org73d7591)
    - [Supplemental Documentation](#orge3e23ab)
  - [sleep\_assay\_wiring](#org7a9f970)
    - [Repository Information](#org44b3fa7)
    - [Images](#orgf6684e0)
    - [Schematic](#orga856cb6)
    - [Gerbers](#orga3b52b3)
    - [Bill of Materials](#orge26c5e5)
    - [Supplemental Documentation](#orga9f69ff)



<a id="org886bb6a"></a>

# Repository Information

-   **Name:** sleep\_assay\_controller
-   **Version:** 2.0
-   **License:** BSD, Open-Source Hardware
-   **URL:** <https://github.com/janelia-modular-devices/sleep_assay_controller>
-   **Author:** Peter Polidoro
-   **Email:** peterpolidoro@gmail.com


<a id="org30c6fbd"></a>

## Description

This device controls the IR and visible backlights in the sleep assay rig along with the backlight cooling fans, white lights, buzzers and indicator lights.


<a id="org2dbc793"></a>

# Images


<a id="orgcabb0db"></a>

# Usage Instructions


<a id="org7bc0b25"></a>

## Arduino Serial Monitor

```sh
# Open terminal, set baud rate to 115200 and set to append newline to
# each request sent to the device.
?
# {
#   "id": "?",
#   "result": {
#     "device_id": {
#       "name": "sleep_assay_controller",
#       "form_factor": "3x2",
#       "serial_number": 0
#     },
#     "api": {
#       "firmware": [
#         "SleepAssayController"
#       ],
#       "verbosity": "NAMES",
#       "functions": [
#         "setIrBacklightAndFanOnAtPower",
#         "setIrBacklightAndFanOnAtIntensity",
#         "setVisibleBacklightAndIndicatorOnAtPower",
#         "setVisibleBacklightAndIndicatorOnAtIntensity",
#         "setWhiteLightAndIndicatorOnAtPower",
#         "setBuzzerAndIndicatorOnAtPower",
#         "getAssayStart",
#         "getAssayEnd",
#         "getAssayDuration",
#         "getExperimentStart",
#         "getExperimentEnd",
#         "getExperimentDuration",
#         "getEntrainmentStart",
#         "getExperimentInfo",
#         "getExperimentDayInfo",
#         "addExperimentDay",
#         "addExperimentDays",
#         "addExperimentDayCopy",
#         "addExperimentDayCopies",
#         "removeLastExperimentDay",
#         "removeAllExperimentDays",
#         "setExperimentDayVisibleBacklight",
#         "setExperimentDayWhiteLight",
#         "setExperimentDayBuzzer",
#         "getAssayStatus"
#       ],
#       "parameters": [
#         "experiment_day",
#         "visible_backlight_delay",
#         "visible_backlight_duration",
#         "buzzer_delay",
#         "buzzer_duration",
#         "day_count"
#       ],
#       "properties": [
#         "visibleBacklightFrequency",
#         "visibleBacklightDutyCycle",
#         "whiteLightEntrainmentPower",
#         "whiteLightRecoveryPower",
#         "whiteLightStartTime",
#         "whiteLightOnDuration",
#         "buzzerOnDurationMin",
#         "buzzerOnDurationMax",
#         "buzzerWaitMin",
#         "buzzerWaitMax",
#         "cameraTriggerFrequency",
#         "entrainmentDuration",
#         "recoveryDuration",
#         "testingDayDuration"
#       ],
#       "callbacks": [
#         "setIrBacklightAndFanOn",
#         "setIrBacklightAndFanOff",
#         "toggleIrBacklightAndFan",
#         "setVisibleBacklightAndIndicatorOn",
#         "setVisibleBacklightAndIndicatorOff",
#         "toggleVisibleBacklightAndIndicator",
#         "setWhiteLightAndIndicatorOn",
#         "setWhiteLightAndIndicatorOff",
#         "toggleWhiteLightAndIndicator",
#         "setBuzzerAndIndicatorOn",
#         "setBuzzerAndIndicatorOff",
#         "toggleBuzzerAndIndicator",
#         "toggleAll",
#         "startCameraTrigger",
#         "stopCameraTrigger",
#         "runAssay",
#         "testAssay",
#         "stopAssay"
#       ]
#     }
#   }
# }
#
# First, set all properties to defaults.
#
setPropertiesToDefaults [ALL]
# {
#   "id": "setPropertiesToDefaults",
#   "result": null
# }
#
# Then get epoch time on the client computer using one of any number of
# ways.
#
# Web Page:
#
# [[https://www.epochconverter.com/]]
#
# Bash: ndate +%s
#
# Example: epoch_time = 1543617175
#
# Set the time on the device:
#
setTime 1543617175
# {
#   "id": "setTime",
#   "result": null
# }
#
# Check the date and time make sure this matches the local date and
# time.
#
now
# {
#   "id": "now",
#   "result": {
#     "year": 2018,
#     "month": 11,
#     "day": 30,
#     "hour": 18,
#     "minute": 32,
#     "second": 56
#   }
# }
#
# If it is off by a few hours, the time zone may need to be adjusted.
#
irBacklightIntensityMax setValue [12]
# {
#   "id": "irBacklightIntensityMax",
#   "result": [
#     12.000000
#   ]
# }
getPropertyValues [SleepAssayController]
# {
#   "id": "getPropertyValues",
#   "result": {
#     "visibleBacklightFrequency": 10.000000,
#     "visibleBacklightDutyCycle": 50,
#     "whiteLightEntrainmentPower": 50,
#     "whiteLightRecoveryPower": 50,
#     "whiteLightStartTime": 9,
#     "whiteLightOnDuration": 12,
#     "buzzerOnDurationMin": 1,
#     "buzzerOnDurationMax": 4,
#     "buzzerWaitMin": 1,
#     "buzzerWaitMax": 3,
#     "cameraTriggerFrequency": 0.500000,
#     "entrainmentDuration": 2,
#     "recoveryDuration": 2,
#     "testingDayDuration": 24
#   }
# }
getAssayDuration
# {
#   "id":"getAssayDuration",
#   "result":4
# }
entrainmentDuration setValue 1
# {
#   "id":"entrainmentDuration",
#   "result":1
# }
recoveryDuration setValue 1
# {
#   "id":"recoveryDuration",
#   "result":1
# }
getAssayDuration
# {
#   "id":"getAssayDuration",
#   "result":2
# }
getExperimentInfo
# {
#   "id":"getExperimentInfo",
#   "result":[]
# }
addExperimentDay
# {
#   "id":"addExperimentDay",
#   "result":0
# }
getExperimentInfo
# {
#   "id": "getExperimentInfo",
#   "result": [
#     {
#       "visible_backlight_intensity": 0.000000,
#       "visible_backlight_delay": 0.000000,
#       "visible_backlight_duration": 0.000000,
#       "white_light_power": 0.000000,
#       "buzzer_power": 0.000000,
#       "buzzer_delay": 0.000000,
#       "buzzer_duration": 0.000000
#     }
#   ]
# }
setExperimentDayVisibleBacklight 0 5.0 0 12
# {
#   "id": "setExperimentDayVisibleBacklight",
#   "result": {
#     "visible_backlight_intensity": 5.000000,
#     "visible_backlight_delay": 0.000000,
#     "visible_backlight_duration": 12.000000,
#     "white_light_power": 75.000000,
#     "buzzer_power": 0.000000,
#     "buzzer_delay": 0.000000,
#     "buzzer_duration": 0.000000
#   }
# }
setExperimentDayWhiteLight 0 75
# {
#   "id": "setExperimentDayWhiteLight",
#   "result": {
#     "visible_backlight_intensity": 0.000000,
#     "visible_backlight_delay": 0.000000,
#     "visible_backlight_duration": 0.000000,
#     "white_light_power": 75.000000,
#     "buzzer_power": 0.000000,
#     "buzzer_delay": 0.000000,
#     "buzzer_duration": 0.000000
#   }
# }
addExperimentDayCopy 0
# {
#   "id":"addExperimentDayCopy",
#   "result":1
# }
setExperimentDayBuzzer 1 50 3 12
# {
#   "id": "setExperimentDayBuzzer",
#   "result": {
#     "visible_backlight_intensity": 5.000000,
#     "visible_backlight_delay": 0.000000,
#     "visible_backlight_duration": 12.000000,
#     "white_light_power": 75.000000,
#     "buzzer_power": 50.000000,
#     "buzzer_delay": 3.000000,
#     "buzzer_duration": 12.000000
#   }
# }
getExperimentInfo
# {
#   "id": "getExperimentInfo",
#   "result": [
#     {
#       "visible_backlight_intensity": 5.000000,
#       "visible_backlight_delay": 0.000000,
#       "visible_backlight_duration": 12.000000,
#       "white_light_power": 75.000000,
#       "buzzer_power": 0.000000,
#       "buzzer_delay": 0.000000,
#       "buzzer_duration": 0.000000
#     },
#     {
#       "visible_backlight_intensity": 5.000000,
#       "visible_backlight_delay": 0.000000,
#       "visible_backlight_duration": 12.000000,
#       "white_light_power": 75.000000,
#       "buzzer_power": 50.000000,
#       "buzzer_delay": 3.000000,
#       "buzzer_duration": 12.000000
#     }
#   ]
# }
getExperimentDuration
# {
#   "id": "getExperimentDuration",
#   "result": 2
# }
getAssayDuration
# {
#   "id": "getAssayDuration",
#   "result": 4
# }
testAssay
# {
#   "id": "testAssay",
#   "result": null
# }
getAssayStatus
# {
#   "id": "getAssayStatus",
#   "result": {
#     "time_now": 1543617266,
#     "date_time_now": {
#       "year": 2018,
#       "month": 11,
#       "day": 30,
#       "hour": 18,
#       "minute": 34,
#       "second": 26
#     },
#     "assay_day": 0.666667,
#     "phase": "ENTRAINMENT",
#     "phase_day": 0.666667,
#     "visible_backlight_intensity": 0.000000,
#     "white_light_power": 50.000000,
#     "buzzer_power": 0.000000,
#     "buzzing": false,
#     "testing": true
#   }
# }
stopAssay
# {
#   "id": "stopAssay",
#   "result": null
# }
runAssay
# {
#   "id": "runAssay",
#   "result": null
# }
getAssayEnd
# {
#   "id": "getAssayEnd",
#   "result": {
#     "year": 2018,
#     "month": 12,
#     "day": 4,
#     "hour": 9,
#     "minute": 0,
#     "second": 0
#   }
# }
stopAssay
# {
#   "id": "stopAssay",
#   "result": null
# }
removeAllExperimentDays
# {
#   "id": "removeAllExperimentDays",
#   "result": null
# }
setIrBacklightAndFanOff
# {
#   "id": "setIrBacklightAndFanOff",
#   "result": null
# }
```


<a id="org02e9623"></a>

## Python

```python
from modular_client import ModularClient
import time

dev = ModularClient()
dev.set_properties_to_defaults(['ALL'])
dev.set_time(int(time.time()))
time_zone_offset = -time.timezone/(60*60)
t = time.time()
if time.localtime(t).tm_isdst and time.daylight:
    time_zone_offset = -time.altzone/(60*60)
    dev.time_zone_offset('setValue',time_zone_offset)
    # -5
dev.now()
# {'year': 2018, 'month': 11, 'day': 30, 'hour': 17, 'minute': 44, 'second': 59}
# check to make sure this matches the local date and time
dev.ir_backlight_intensity_max('setValue',12);
# 12
dev.get_property_values(['SleepAssayController'])
# {'visibleBacklightFrequency': 10.0,
#  'visibleBacklightDutyCycle': 50,
#  'whiteLightEntrainmentPower': 50,
#  'whiteLightRecoveryPower': 50,
#  'whiteLightStartTime': 9,
#  'whiteLightOnDuration': 12,
#  'buzzerOnDurationMin': 1,
#  'buzzerOnDurationMax': 4,
#  'buzzerWaitMin': 1,
#  'buzzerWaitMax': 3,
#  'cameraTriggerFrequency': 0.5,
#  'entrainmentDuration': 2,
#  'recoveryDuration': 2,
#  'testingDayDuration': 24}
dev.get_assay_duration()
# 4
dev.entrainment_duration('setValue',1)
# 1
dev.recovery_duration('setValue',1)
# 1
dev.get_assay_duration()
# 2
dev.get_experiment_info()
# []
dev.add_experiment_day()
# 0
dev.get_experiment_info()
# [{'visible_backlight_intensity': 0.0,
#   'visible_backlight_delay': 0.0,
#   'visible_backlight_duration': 0.0,
#   'white_light_power': 0.0,
#   'buzzer_power': 0.0,
#   'buzzer_delay': 0.0,
#   'buzzer_duration': 0.0}]
experiment_day = 0
visible_backlight_intensity = 5.0
visible_backlight_delay = 0
visible_backlight_duration = 12
dev.set_experiment_day_visible_backlight(experiment_day,
                                         visible_backlight_intensity,
                                         visible_backlight_delay,
                                         visible_backlight_duration)
# {'visible_backlight_intensity': 5.0,
#  'visible_backlight_delay': 0.0,
#  'visible_backlight_duration': 12.0,
#  'white_light_power': 75.0,
#  'buzzer_power': 0.0,
#  'buzzer_delay': 0.0,
#  'buzzer_duration': 0.0}
white_light_power = 75
dev.set_experiment_day_white_light(experiment_day,white_light_power)
# {'visible_backlight_intensity': 0.0,
#  'visible_backlight_delay': 0.0,
#  'visible_backlight_duration': 0.0,
#  'white_light_power': 75.0,
#  'buzzer_power': 0.0,
#  'buzzer_delay': 0.0,
#  'buzzer_duration': 0.0}
dev.add_experiment_day_copy(0)
# 1
experiment_day = 1
buzzer_power = 50
buzzer_delay = 3
buzzer_duration = 12
dev.set_experiment_day_buzzer(experiment_day,
                              buzzer_power,
                              buzzer_delay,
                              buzzer_duration)
# {'visible_backlight_intensity': 5.0,
#  'visible_backlight_delay': 0.0,
#  'visible_backlight_duration': 12.0,
#  'white_light_power': 75.0,
#  'buzzer_power': 50.0,
#  'buzzer_delay': 3.0,
#  'buzzer_duration': 12.0}
dev.get_experiment_info()
# [{'visible_backlight_intensity': 5.0,
#   'visible_backlight_delay': 0.0,
#   'visible_backlight_duration': 12.0,
#   'white_light_power': 75.0,
#   'buzzer_power': 0.0,
#   'buzzer_delay': 0.0,
#   'buzzer_duration': 0.0},
#  {'visible_backlight_intensity': 5.0,
#   'visible_backlight_delay': 0.0,
#   'visible_backlight_duration': 12.0,
#   'white_light_power': 75.0,
#   'buzzer_power': 50.0,
#   'buzzer_delay': 3.0,
#   'buzzer_duration': 12.0}]
dev.get_experiment_duration()
# 2
dev.get_assay_duration()
# 4
dev.test_assay()
dev.get_assay_status()
# {'time_now': 1543618497,
#  'date_time_now': {'year': 2018,
#   'month': 11,
#   'day': 30,
#   'hour': 17,
#   'minute': 54,
#   'second': 57},
#  'assay_day': 0.666667,
#  'phase': 'ENTRAINMENT',
#  'phase_day': 0.666667,
#  'visible_backlight_intensity': 0.000000,
#  'white_light_power': 50.000000,
#  'buzzer_power': 0.000000,
#  'buzzing': False,
#  'testing': True}
dev.stop_assay()
dev.run_assay()
dev.get_assay_end()
# {'year': 2018, 'month': 12, 'day': 4, 'hour': 9, 'minute': 0, 'second': 0}
dev.stop_assay()
dev.remove_all_experiment_days()
dev.set_ir_backlight_and_fan_off()
```


<a id="orgdf850e3"></a>

## Matlab

```matlab
getAvailableComPorts()
serial_port = 'COM9'; % example
dev = ModularClient(serial_port);
dev.open();
dev.setPropertiesToDefaults({'ALL'});
% look up time zone offset for your location
% taking into account daylight savings time
% if necessary
% e.g.
% U.S. Eastern = -5
% U.S. Eastern daylight savings = -4
time_zone_offset = -4;
dev.timeZoneOffset('setValue',time_zone_offset);
dev.setTime(etime(clock,[1970,1,1,0,0,0]));
n = dev.now();
t = clock;
dev.adjustTime((t(4) - n.hour)*60*60);
dev.now()
%   year: 2018
%  month: 11
%    day: 30
%   hour: 17
% minute: 44
% second: 59
% check to make sure this matches the local date and time
dev.irBacklightIntensityMax('setValue',12)
% 12
dev.getPropertyValues({'SleepAssayController'})
%  visibleBacklightFrequency: 10.0
%  visibleBacklightDutyCycle: 50
% whiteLightEntrainmentPower: 50
%    whiteLightRecoveryPower: 50
%        whiteLightStartTime: 9
%       whiteLightOnDuration: 12
%        buzzerOnDurationMin: 1
%        buzzerOnDurationMax: 4
%              buzzerWaitMin: 1
%              buzzerWaitMax: 3
%     cameraTriggerFrequency: 0.5
%        entrainmentDuration: 2
%           recoveryDuration: 2
%         testingDayDuration: 24
dev.getAssayDuration()
% 4
dev.entrainmentDuration('setValue',1);
dev.recoveryDuration('setValue',1);
dev.getAssayDuration()
% 2
dev.getExperimentInfo()
% Empty cell array: 0-by-1
dev.addExperimentDay()
% 0
info = dev.getExperimentInfo();
info{1}
% visible_backlight_intensity: 0.0
%     visible_backlight_delay: 0.0
%  visible_backlight_duration: 0.0
%           white_light_power: 0.0
%                buzzer_power: 0.0
%                buzzer_delay: 0.0
%             buzzer_duration: 0.0
experiment_day = 0;
visible_backlight_intensity = 5.0;
visible_backlight_delay = 0;
visible_backlight_duration = 12;
dev.setExperimentDayVisibleBacklight(experiment_day, ...
                                     visible_backlight_intensity, ...
                                     visible_backlight_delay, ...
                                     visible_backlight_duration);
white_light_power = 75;
dev.setExperimentDayWhiteLight(experiment_day,white_light_power);
dev.addExperimentDayCopy(0)
% 1
experiment_day = 1;
buzzer_power = 50;
buzzer_delay = 3;
buzzer_duration = 12;
dev.setExperimentDayBuzzer(experiment_day, ...
                           buzzer_power, ...
                           buzzer_delay, ...
                           buzzer_duration);
info = dev.getExperimentInfo();
info{2}
% visible_backlight_intensity: 5.0
%     visible_backlight_delay: 0.0
%  visible_backlight_duration: 12.0
%           white_light_power: 75.0
%                buzzer_power: 50.0
%                buzzer_delay: 3.0
%             buzzer_duration: 12.0
dev.getExperimentDuration()
% 2
dev.getAssayDuration()
% 4
dev.testAssay();
dev.getAssayStatus()
%                    time_now: 1543618497
%               date_time_now: [1x1 struct]
%                   assay_day: 0.666667
%                       phase: 'ENTRAINMENT'
%                   phase_day: 0.666667
% visible_backlight_intensity: 0
%           white_light_power: 50
%                buzzer_power: 0
%                     buzzing: 0
%                     testing: 1
dev.runAssay();
dev.getAssayEnd()
%   year: 2018
%  month: 12
%    day: 4
%   hour: 9
% minute: 0
% second: 0
dev.stopAssay()
dev.removeAllExperimentDays()
dev.setIrBacklightAndFanOff()
```


<a id="orgdfb3080"></a>

# Build Instructions


<a id="orgc9742b9"></a>

# Software


<a id="orgd99c6ec"></a>

# Firmware


<a id="orgd7c3fe5"></a>

## BacklightController


<a id="org6a7eb5e"></a>

### Library Information

-   **Name:** BacklightController
-   **Version:** 4.0.2
-   **License:** BSD
-   **URL:** <https://github.com/janelia-arduino/BacklightController>
-   **Author:** Peter Polidoro
-   **Email:** peterpolidoro@gmail.com

1.  Description

    Modular device backlight controller library.


<a id="orgaf34bff"></a>

### API NAMES

```js
{
  "id": "getApi",
  "result": {
    "firmware": [
      "BacklightController"
    ],
    "verbosity": "NAMES",
    "functions": [
      "setAllIrBacklightsOnAtPower",
      "setAllIrBacklightsOnAtIntensity",
      "setIrBacklightOn",
      "setIrBacklightOnAtPower",
      "setIrBacklightOnAtIntensity",
      "setIrBacklightOff",
      "toggleIrBacklight",
      "getIrBacklightPowersWhenOn",
      "getIrBacklightIntensitiesWhenOn",
      "getIrBacklightPowers",
      "getIrBacklightIntensities",
      "getIrBacklightPowerBounds",
      "getIrBacklightIntensityBounds",
      "irBacklightPowerToIntensities",
      "irBacklightIntensityToPowers",
      "setAllVisibleBacklightsOnAtPower",
      "setAllVisibleBacklightsOnAtIntensity",
      "setVisibleBacklightOn",
      "setVisibleBacklightOnAtPower",
      "setVisibleBacklightOnAtIntensity",
      "setVisibleBacklightOff",
      "toggleVisibleBacklight",
      "getVisibleBacklightPowersWhenOn",
      "getVisibleBacklightIntensitiesWhenOn",
      "getVisibleBacklightPowers",
      "getVisibleBacklightIntensities",
      "getVisibleBacklightPowerBounds",
      "getVisibleBacklightIntensityBounds",
      "visibleBacklightPowerToIntensities",
      "visibleBacklightIntensityToPowers",
      "setAllHighVoltagesOnAtPower",
      "setHighVoltageOn",
      "setHighVoltageOnAtPower",
      "setHighVoltageOff",
      "toggleHighVoltage",
      "getHighVoltagePowersWhenOn",
      "getHighVoltagePowers",
      "getHighVoltagePowerBounds",
      "setAllLowVoltagesOnAtPower",
      "setLowVoltageOn",
      "setLowVoltageOnAtPower",
      "setLowVoltageOff",
      "toggleLowVoltage",
      "getLowVoltagePowersWhenOn",
      "getLowVoltagePowers",
      "getLowVoltagePowerBounds"
    ],
    "parameters": [
      "intensity",
      "ir_backlight",
      "visible_backlight",
      "high_voltage",
      "low_voltage"
    ],
    "properties": [
      "irBacklightPowerToIntensityRatio",
      "irBacklightIntensityMax",
      "visibleBacklightPowerToIntensityRatio",
      "visibleBacklightIntensityMax",
      "highVoltagePowerMax",
      "lowVoltagePowerMax",
      "irBacklightSwitchingFrequencyMax",
      "visibleBacklightSwitchingFrequencyMax",
      "highVoltageSwitchingFrequencyMax",
      "lowVoltageSwitchingFrequencyMax"
    ],
    "callbacks": [
      "setAllIrBacklightsOn",
      "setAllIrBacklightsOff",
      "toggleAllIrBacklights",
      "setAllVisibleBacklightsOn",
      "setAllVisibleBacklightsOff",
      "toggleAllVisibleBacklights",
      "setAllHighVoltagesOn",
      "setAllHighVoltagesOff",
      "toggleAllHighVoltages",
      "setAllLowVoltagesOn",
      "setAllLowVoltagesOff",
      "toggleAllLowVoltages"
    ]
  }
}
```


<a id="org665d9b4"></a>

### API GENERAL

<./firmware/BacklightController/api/>


<a id="orgc6151b5"></a>

### Ancestors

<https://github.com/janelia-arduino/ModularServer>

<https://github.com/janelia-arduino/ModularDeviceBase>

<https://github.com/janelia-arduino/DigitalController>


<a id="org1a261ea"></a>

### Clients


<a id="org80cbebd"></a>

### Devices

<https://github.com/janelia-modular-devices/modular_device_base>

<https://github.com/janelia-modular-devices/backlight_controller>


<a id="org5692dd0"></a>

### More Detailed Modular Device Information

<https://github.com/janelia-modular-devices/modular-devices>


<a id="org913fa5d"></a>

### Installation Instructions

<https://github.com/janelia-arduino/arduino-libraries>


<a id="org62d9d64"></a>

## DigitalController


<a id="org37d32f6"></a>

### Library Information

-   **Name:** DigitalController
-   **Version:** 2.2.1
-   **License:** BSD
-   **URL:** <https://github.com/janelia-arduino/DigitalController>
-   **Author:** Peter Polidoro
-   **Email:** peterpolidoro@gmail.com

1.  Description

    Modular device digital output controller library.


<a id="orgc62fd8e"></a>

### API NAMES

```js
{
  "id": "getApi",
  "result": {
    "firmware": [
      "DigitalController"
    ],
    "verbosity": "NAMES",
    "functions": [
      "allEnabled",
      "setPowerWhenOn",
      "setPowersWhenOn",
      "setAllPowersWhenOn",
      "setAllPowersWhenOnToMax",
      "getPowersWhenOn",
      "getPowers",
      "setChannelOn",
      "setChannelOnAtPower",
      "setChannelOff",
      "setChannelsOn",
      "setChannelsOnAtPower",
      "setChannelsOff",
      "toggleChannel",
      "toggleChannels",
      "setAllChannelsOnAtPower",
      "setChannelOnAllOthersOff",
      "setChannelOffAllOthersOn",
      "setChannelsOnAllOthersOff",
      "setChannelsOffAllOthersOn",
      "channelIsOn",
      "getChannelsOn",
      "getChannelsOff",
      "getChannelCount",
      "addPwm",
      "startPwm",
      "addRecursivePwm",
      "startRecursivePwm",
      "stopPwm",
      "stopAllPwm",
      "getChannelsPwmIndexes",
      "getPwmInfo",
      "getPowerBounds"
    ],
    "parameters": [
      "channel",
      "channels",
      "power",
      "powers",
      "delay",
      "period",
      "on_duration",
      "count",
      "pwm_index",
      "periods",
      "on_durations"
    ],
    "properties": [
      "channelCount",
      "powerMax"
    ],
    "callbacks": [
      "enableAll",
      "disableAll",
      "toggleAllChannels",
      "setAllChannelsOn",
      "setAllChannelsOff"
    ]
  }
}
```


<a id="org7314b4f"></a>

### API GENERAL

<./firmware/DigitalController/api/>


<a id="org4b9eb1f"></a>

### Ancestors

<https://github.com/janelia-arduino/ModularServer>

<https://github.com/janelia-arduino/ModularDeviceBase>


<a id="org6bcc961"></a>

### Clients


<a id="org7d3e0ce"></a>

### Devices

<https://github.com/janelia-modular-devices/modular_device_base>


<a id="orgb81ac3e"></a>

### More Detailed Modular Device Information

<https://github.com/janelia-modular-devices/modular-devices>


<a id="org7f9e787"></a>

### Installation Instructions

<https://github.com/janelia-arduino/arduino-libraries>


<a id="org4159958"></a>

## SleepAssayController


<a id="org82a005d"></a>

### Library Information

-   **Name:** SleepAssayController
-   **Version:** 2.0.0
-   **License:** BSD
-   **URL:** <https://github.com/janelia-arduino/SleepAssayController>
-   **Author:** Peter Polidoro
-   **Email:** peterpolidoro@gmail.com

1.  Description

    Modular device sleep assay controller library.


<a id="orgded87b0"></a>

### API NAMES

```js
{
  "id": "getApi",
  "result": {
    "firmware": [
      "SleepAssayController"
    ],
    "verbosity": "NAMES",
    "functions": [
      "setIrBacklightAndFanOnAtPower",
      "setIrBacklightAndFanOnAtIntensity",
      "setVisibleBacklightAndIndicatorOnAtPower",
      "setVisibleBacklightAndIndicatorOnAtIntensity",
      "setWhiteLightAndIndicatorOnAtPower",
      "setBuzzerAndIndicatorOnAtPower",
      "getAssayStart",
      "getAssayEnd",
      "getAssayDuration",
      "getExperimentStart",
      "getExperimentEnd",
      "getExperimentDuration",
      "getEntrainmentStart",
      "getExperimentInfo",
      "getExperimentDayInfo",
      "addExperimentDay",
      "addExperimentDays",
      "addExperimentDayCopy",
      "addExperimentDayCopies",
      "removeLastExperimentDay",
      "removeAllExperimentDays",
      "setExperimentDayVisibleBacklight",
      "setExperimentDayWhiteLight",
      "setExperimentDayBuzzer",
      "getAssayStatus"
    ],
    "parameters": [
      "experiment_day",
      "visible_backlight_delay",
      "visible_backlight_duration",
      "buzzer_delay",
      "buzzer_duration",
      "day_count"
    ],
    "properties": [
      "visibleBacklightFrequency",
      "visibleBacklightDutyCycle",
      "whiteLightEntrainmentPower",
      "whiteLightRecoveryPower",
      "whiteLightStartTime",
      "whiteLightOnDuration",
      "buzzerOnDurationMin",
      "buzzerOnDurationMax",
      "buzzerWaitMin",
      "buzzerWaitMax",
      "cameraTriggerFrequency",
      "entrainmentDuration",
      "recoveryDuration",
      "testingDayDuration"
    ],
    "callbacks": [
      "setIrBacklightAndFanOn",
      "setIrBacklightAndFanOff",
      "toggleIrBacklightAndFan",
      "setVisibleBacklightAndIndicatorOn",
      "setVisibleBacklightAndIndicatorOff",
      "toggleVisibleBacklightAndIndicator",
      "setWhiteLightAndIndicatorOn",
      "setWhiteLightAndIndicatorOff",
      "toggleWhiteLightAndIndicator",
      "setBuzzerAndIndicatorOn",
      "setBuzzerAndIndicatorOff",
      "toggleBuzzerAndIndicator",
      "toggleAll",
      "startCameraTrigger",
      "stopCameraTrigger",
      "runAssay",
      "testAssay",
      "stopAssay"
    ]
  }
}
```


<a id="org0e111c4"></a>

### API GENERAL

<./firmware/SleepAssayController/api/>


<a id="org0b1cb98"></a>

### Ancestors

<https://github.com/janelia-arduino/ModularServer>

<https://github.com/janelia-arduino/ModularDeviceBase>

<https://github.com/janelia-arduino/DigitalController>

<https://github.com/janelia-arduino/BacklightController>


<a id="org9789570"></a>

### Clients


<a id="org1b96a96"></a>

### Devices

<https://github.com/janelia-modular-devices/modular_device_base>

<https://github.com/janelia-modular-devices/backlight_controller>

<https://github.com/janelia-modular-devices/sleep_assay_controller>


<a id="org0e5d6f4"></a>

### More Detailed Modular Device Information

<https://github.com/janelia-modular-devices/modular-devices>


<a id="org38d34b3"></a>

### Installation Instructions

<https://github.com/janelia-arduino/arduino-libraries>


<a id="orgc75dbcc"></a>

# Hardware


<a id="org5e67c8e"></a>

## backlight\_controller\_3x2


<a id="org00e12f0"></a>

### Repository Information

-   **Name:** backlight\_controller\_3x2
-   **Version:** 1.2
-   **License:** Open-Source Hardware
-   **URL:** <https://github.com/janelia-kicad/backlight_controller_3x2>
-   **Author:** Peter Polidoro
-   **Email:** peterpolidoro@gmail.com

1.  Description

    This board controls one Smart Vision backlight with IR and visible channels plus additional high and low power channel outputs.


<a id="orgae57cdb"></a>

### Images


<a id="org7bc1d0f"></a>

### Schematic

[./hardware/backlight\_controller\_3x2/schematic/backlight\_controller\_3x2.pdf](./hardware/backlight_controller_3x2/schematic/backlight_controller_3x2.pdf)

![img](./images/backlight_controller_3x2/schematic/images/schematic00.png)

![img](./images/backlight_controller_3x2/schematic/images/schematic01.png)

![img](./images/backlight_controller_3x2/schematic/images/schematic02.png)

![img](./images/backlight_controller_3x2/schematic/images/schematic03.png)

![img](./images/backlight_controller_3x2/schematic/images/schematic04.png)

![img](./images/backlight_controller_3x2/schematic/images/schematic05.png)

![img](./images/backlight_controller_3x2/schematic/images/schematic06.png)

![img](./images/backlight_controller_3x2/schematic/images/schematic07.png)

![img](./images/backlight_controller_3x2/schematic/images/schematic08.png)

![img](./images/backlight_controller_3x2/schematic/images/schematic09.png)

![img](./images/backlight_controller_3x2/schematic/images/schematic10.png)

![img](./images/backlight_controller_3x2/schematic/images/schematic11.png)

![img](./images/backlight_controller_3x2/schematic/images/schematic12.png)

![img](./images/backlight_controller_3x2/schematic/images/schematic13.png)

![img](./images/backlight_controller_3x2/schematic/images/schematic14.png)


<a id="orgcfdda6f"></a>

### Gerbers

Send gerbers zip file to your favorite PCB manufacturer for fabrication.

[./hardware/backlight\_controller\_3x2/gerbers/backlight\_controller\_3x2\_v1.2.zip](./hardware/backlight_controller_3x2/gerbers/backlight_controller_3x2_v1.2.zip)

![img](./images/backlight_controller_3x2/gerbers/images/gerbers00.png)

![img](./images/backlight_controller_3x2/gerbers/images/gerbers01.png)


<a id="org73d7591"></a>

### Bill of Materials

1.  PCB Parts

    | Item | Reference(s)                    | Quantity | PartNumber         | Vendor  | Description                                                               |
    |---- |------------------------------- |-------- |------------------ |------- |------------------------------------------------------------------------- |
    | 1    | C1 C2 C3 C4 C5 C6               | 6        | 399-13229-1-ND     | digikey | CAP CER 0.1UF 50V 10% X7R 1210                                            |
    | 2    | D1                              | 1        | 568-11697-1-ND     | digikey | DIODE SCHOTTKY 45V 10A CFP15                                              |
    | 3    | HPS1 HPS2 HPS3 HPS4             | 4        | BTS3256DAUMA1CT-ND | digikey | IC SWITCH SMART LOWSIDE TO252-5                                           |
    | 4    | J1                              | 1        | 1195-4005-1-ND     | digikey | CONN D-SUB RCPT 9POS SMD SOLDER                                           |
    | 5    | J2                              | 1        | 1195-4006-1-ND     | digikey | CONN D-SUB PLUG 9POS SMD SOLDER                                           |
    | 6    | J3 J4                           | 2        | 277-10282-1-ND     | digikey | CONN FMALE INSERT 5POS SOLDER                                             |
    | 7    | L1                              | 1        | 350-1723-ND        | digikey | LED 2MM 24V VERTICAL RED PC MNT                                           |
    | 8    | L10 L11 L2 L3 L4 L5 L6 L7 L8 L9 | 10       | 350-1726-ND        | digikey | LED 2MM 5V VERTICAL GREEN PC MNT                                          |
    | 9    | MDB1                            | 2        | S1011E-16-ND       | digikey | 16 Position Header Through Hole Male Pins                                 |
    | 10   | P1                              | 1        | WM1353-ND          | digikey | CONN HEADER 6POS 4.2MM R/A TIN                                            |
    | 11   | R1 R2 R3 R4                     | 4        | P5.90KAACT-ND      | digikey | RES SMD 5.9k OHM 1% 1/2W 1210                                             |
    | 12   | R5 R6 R7 R8                     | 4        | P75.0CCT-ND        | digikey | RES SMD 75 OHM 1% 1/8W 0805                                               |
    | 13   | U1 U2                           | 2        | 296-14668-1-ND     | digikey | Buffer Non-Inverting 1 Element 8 Bit per Element Push-Pull Output 20-SOIC |
    | 14   | U3 U4                           | 2        | NUD3124LT1GOSCT-ND | digikey | IC INDCT LOAD DRVR AUTO SOT23                                             |

2.  Supplemental Parts

    | Item | Quantity | PartNumber   | Vendor  | Description                    |
    |---- |-------- |------------ |------- |------------------------------ |
    | 1    | 1        | 1866-2122-ND | digikey | AC/DC DESKTOP ADAPTER 24V 280W |
    | 2    | 1        | 1866-5006-ND | digikey | CORD IEC 320-C13 6FT BLACK     |
    | 3    | 2        | 277-10308-ND | digikey | CONN INSERT SHELL PRESS FIT    |

3.  Vendor Parts Lists

    [./hardware/backlight\_controller\_3x2/bom/digikey\_parts.csv](./hardware/backlight_controller_3x2/bom/digikey_parts.csv)

    [./hardware/backlight\_controller\_3x2/bom/supplemental\_digikey\_parts.csv](./hardware/backlight_controller_3x2/bom/supplemental_digikey_parts.csv)


<a id="orge3e23ab"></a>

### Supplemental Documentation

1.  Assembly Instructions

    -   Solder surface mount and through hole components onto the pcb.


<a id="org7a9f970"></a>

## sleep\_assay\_wiring


<a id="org44b3fa7"></a>

### Repository Information

-   **Name:** sleep\_assay\_wiring
-   **Version:** 1.0
-   **License:** Open-Source Hardware
-   **URL:** <https://github.com/janelia-kicad/sleep_assay_wiring>
-   **Author:** Peter Polidoro
-   **Email:** peterpolidoro@gmail.com

1.  Description


<a id="orgf6684e0"></a>

### Images


<a id="orga856cb6"></a>

### Schematic

[./hardware/sleep\_assay\_wiring/schematic/sleep\_assay\_wiring.pdf](./hardware/sleep_assay_wiring/schematic/sleep_assay_wiring.pdf)

![img](./images/sleep_assay_wiring/schematic/images/schematic00.png)


<a id="orga3b52b3"></a>

### Gerbers


<a id="orge26c5e5"></a>

### Bill of Materials

1.  PCB Parts

    | Item | Reference(s)    | Quantity | PartNumber     | Vendor            | Description                                                     |
    |---- |--------------- |-------- |-------------- |----------------- |--------------------------------------------------------------- |
    | 1    | BL1             | 1        | MOBL\_300x300  | smartvisionlights | Maximum Operating Backlight 300x300                             |
    | 2    | CABLE1 CABLE2   | 2        | 277-8345-ND    | digikey           | CBL FMALE RA TO MALE 5POS 1.5M                                  |
    | 3    | CABLE3 CABLE4   | 2        | 1195-7211-ND   | digikey           | CABLE ASSY DB09 SHLD BEIGE 2M                                   |
    | 4    | CABLE5          | 1        | ACC-01-3000    | flir              | FLIR camera 8 pins 1m GPIO Cable Hirose HR25 Circular Connector |
    | 5    | CABLE6          | 1        | GC14333-ND     | digikey           | USB3.0-A-USB3.0-MICRO-B 3M GOLD                                 |
    | 6    | CAMERA1         | 1        | FL3-U3-13Y3M-C | flir              | 1280x1024 150 FPS Mono                                          |
    | 7    | D1 D2 D3        | 3        | 751-1213-ND    | digikey           | EMITTER IR 850NM 100MA RADIAL                                   |
    | 8    | F1 F2 F3 F4     | 4        | 381-2367-ND    | digikey           | FAN AXIAL 40X10MM 24VDC WIRE                                    |
    | 9    | FR1             | 1        | 289-1240-ND    | digikey           | LED FLEX RIBBON 24V WHT 4M                                      |
    | 10   | J1              | 1        | 277-2667-ND    | digikey           | CONN DSUB PLUG 9POS STR TERM BLK                                |
    | 11   | J2              | 1        | 277-2668-ND    | digikey           | CONN DSUB RCPT 9POS STR TERM BLK                                |
    | 12   | VM1 VM2 VM3 VM4 | 4        | 1670-1026-ND   | digikey           | VIBRATION MOTOR CYL 5V WIRE                                     |

2.  Supplemental Parts

    | Item | Quantity | PartNumber  | Vendor  | Description                    |
    |---- |-------- |----------- |------- |------------------------------ |
    | 1    | 3        | 492-1782-ND | digikey | LED HOLDER PNL CLIP 5MM BK NYL |
    |      |          |             |         |                                |

3.  Vendor Parts Lists

    [./hardware/sleep\_assay\_wiring/bom/digikey\_parts.csv](./hardware/sleep_assay_wiring/bom/digikey_parts.csv)

    [./hardware/sleep\_assay\_wiring/bom/flir\_parts.csv](./hardware/sleep_assay_wiring/bom/flir_parts.csv)

    [./hardware/sleep\_assay\_wiring/bom/smartvisionlights\_parts.csv](./hardware/sleep_assay_wiring/bom/smartvisionlights_parts.csv)

    [./hardware/sleep\_assay\_wiring/bom/supplemental\_digikey\_parts.csv](./hardware/sleep_assay_wiring/bom/supplemental_digikey_parts.csv)


<a id="orga9f69ff"></a>

### Supplemental Documentation

1.  Assembly Instructions
