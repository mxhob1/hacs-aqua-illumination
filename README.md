# AquaIllumination Lights

Support for a range of aquarium lights, from AquaIllumination.

Based on top of one of a python modules @mcclown wrote, [AquaIPy](https://github.com/mcclown/AquaIPy). There is no documented API for AquaIllumination lights, so this all had to be reverse-engineered.

A brief rundown of features/caveats:

* This component implements 3 different types of platforms, for each light. A schedule enabled switch, a light for each channel and a sensor for each channel.
* Each individual light channel appears as a different light entity.
* Each individual light channel also has a corresponding sensor entity, with the brightness level. This is useful for graphing the light channel levels.
* It is possible to turn off the "scheduled mode" for the light but if it isn't turned off, then light brightness changes will appear for a few seconds then change back to the normal schedule.
* Support is only for the HD range of lights. No support for earlier models yet.
* No support for setting more than one channel at once.
* No support for increasing the channels to over 100% (the HD range). Although a schedule can still set values over 100%.

A sample configuration is shown below. This adds a light entity for each of the colour channels called <name>_<channel name>.

```YAML
aquaillumination:
  - host: 192.168.1.100
    name: sump ai
  - host: 192.168.1.101
    name: dt ai
```

@mcclown was been using this component with [this](https://github.com/thomasloven/lovelace-slider-entity-row) custom lovelace entity. A sample lovelace configuration for this component is below, showing how multiple light entities are created.

```YAML

entities:
  - entity: light.sump_ai_uv
    step: 1
    type: 'custom:slider-entity-row'
  - entity: light.sump_ai_violet
    step: 1
    type: 'custom:slider-entity-row'
  - entity: light.sump_ai_royal
    step: 1
    type: 'custom:slider-entity-row'
  - entity: light.sump_ai_blue
    step: 1
    type: 'custom:slider-entity-row'
  - entity: light.sump_ai_green
    step: 1
    type: 'custom:slider-entity-row'
  - entity: light.sump_ai_deep_red
    step: 1
    type: 'custom:slider-entity-row'
  - entity: light.sump_ai_cool_white
    step: 1
    type: 'custom:slider-entity-row'
title: Sump Prime HD
type: entities
```
