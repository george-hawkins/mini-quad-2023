ExpressLRS preset
=================

Using the _ExpressLRS 250Hz_ preset, I tried all the different preset options to see what they changed.

I chose the 250Hz one for my experimentation for no better reason than that it's somewhere in-between the 50Hz and 500Hz bounds.

##### Fine tuning

The options in the _Fine Tuning_ section modify all or some of the following settings (their default values are shown here):

```
set feedforward_boost = 15
set feedforward_jitter_factor = 7
set feedforward_smooth_factor = 25
set rc_smoothing_auto_factor = 30
set rc_smoothing_auto_factor_throttle = 30
set rc_smoothing_auto_factor_throttle = 30
set rc_smoothing_feedforward_cutoff = 0
set rc_smoothing_setpoint_cutoff = 0
set rc_smoothing_throttle_cutoff = 0
```

Following are the settings that each of the fine tuning options changed. As you can see _freestyle_ is the one that diverges least from the defaults.

250Hz racing:

```
set rc_smoothing_auto_factor = 25
set rc_smoothing_auto_factor_throttle = 25
set feedforward_smooth_factor = 35
set feedforward_jitter_factor = 4
set feedforward_boost = 18
```

250Hz freestyle:

```
set rc_smoothing_auto_factor = 52
set feedforward_jitter_factor = 8
```

250Hz freestyle HD:

```
set rc_smoothing_auto_factor = 140
set rc_smoothing_setpoint_cutoff = 25
set rc_smoothing_feedforward_cutoff = 25
set feedforward_jitter_factor = 10
```

250Hz cinematic:

```
set rc_smoothing_auto_factor = 250
set rc_smoothing_auto_factor_throttle = 170
set rc_smoothing_setpoint_cutoff = 12
set rc_smoothing_feedforward_cutoff = 12
set rc_smoothing_throttle_cutoff = 20
set feedforward_smooth_factor = 60
set feedforward_jitter_factor = 12
```

250Hz cinematic ultra:

```
set rc_smoothing_auto_factor = 250                                                                  
set rc_smoothing_auto_factor_throttle = 170                                                         
set rc_smoothing_setpoint_cutoff = 6                                                                
set rc_smoothing_feedforward_cutoff = 6                                                             
set rc_smoothing_throttle_cutoff = 20
set feedforward_smooth_factor = 65
set feedforward_jitter_factor = 15
```

It's hard to find out what the implications of any of these settings are except by looking at the relevant PRs, e.g. [PR #7085](https://github.com/betaflight/betaflight/pull/7085) for `rc_smoothing_auto_factor`.

##### Connection method

In the _ELRS Rx connection method_ section, choosing _Serial, separated Rx_ (which is the setup we have) results in:

```
feature RX_SERIAL
```

This is already the default (and so results in no changes).

_SPI, on the FC_ results in:

```
feature -RX_SERIAL
feature RX_SPI
set rx_spi_protocol = EXPRESSLRS
```

##### Voltage telemetry

In the _Voltage telemetry reading_ section, choosing _Whole pack values_ results in:

```
set report_cell_voltage = OFF
```

This is already the default. Choosing _Single Cell values_ sets `report_cell_voltage` to `ON`.
