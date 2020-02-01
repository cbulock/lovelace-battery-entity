
# Lovelace Battery Entity


A custom [Lovelace](https://www.home-assistant.io/lovelace/) component for displaying battery levels for battery entities for [Home Assistant](https://github.com/home-assistant/home-assistant).

<img src="https://raw.githubusercontent.com/cbulock/lovelace-battery-entity/master/images/screenshot.png" width="300">

## Install

### Simple install

1. Download and copy [battery-entity.js](https://raw.githubusercontent.com/cbulock/lovelace-battery-entity/master/battery-entity.js) into your `config/www` directory.

2. Add a reference to `battery-entity.js` inside your `ui-lovelace.yaml`.

  ```yaml
  resources:
    - url: /local/battery-entity.js?v=0.1
      type: module
  ```

### Installation using Git
**Clone this repository into your `config/www` folder using git.**

 ```console
$ git clone https://github.com/cbulock/lovelace-battery-entity.git
```

**Add a reference to the card in your `ui-lovelace.yaml`.**

```yaml
resources:
  - url: /local/lovelace-battery-entity/battery-entity.js?v=1
    type: module
```

### *(Optional)* Add to custom updater

1. Make sure you've the [custom_updater](https://github.com/custom-components/custom_updater) component installed and working.

2. Add a new reference under `card_urls` in your `custom_updater` configuration in `configuration.yaml`.

  ```yaml
  custom_updater:
    card_urls:
      - https://raw.githubusercontent.com/cbulock/lovelace-battery-entity/master/battery-entity.js
  ```

## Updating
1. Find your `battery-entity.js` file in `config/www` or wherever you ended up storing it.

2. Replace the local file with the latest one attached in the here: [battery-entity.js](https://raw.githubusercontent.com/cbulock/lovelace-battery-entity/master/battery-entity.js).

3. Add the new version number to the end of the cards reference url in your `ui-lovelace.yaml` like below.

  ```yaml
  resources:
    - url: /local/battery-entity.js?v=0.2
      type: module
  ```

*You may need to empty the browsers cache if you have problems loading the updated card.*

## Using the card

### Options

#### Card options
| Name | Type | Default | Since | Default | Description |
|------|------|---------|-------|---------|-------------|
| type | string | **required** | v0.1 | | `custom:battery-entity`
| entity | string | **required** | v0.1 | | An entity_id that has a percentage as a state.
| attribute | string | optional | v0.2 | battery,battery_level,state | defines a list of attributes to obtain the battery level from (attributes will be checked in order separated by commas)
| name | string | optional | v0.1 | *friendly_name* | Override the entities friendly name.
| warning | integer | optional | v0.1 | 35 | Sets the level at which the battery icon will be shown as yellow.
| critical | integer | optional | v0.1 | 15 | Sets the level at which the battery icon will be shown as red.



### Example usage

```yaml
- type: custom:battery-entity
  entity: sensor.front_door_lock_battery
  attributes: battery,battery_level,batterypercent,state
```

#### Use with [Auto Entities](https://github.com/thomasloven/lovelace-auto-entities)
If you use Auto Entities card and want to add all of the battery & battery_level attributes automatically you can do so as follows:

```yaml
card:
  show_header_toggle: false
  type: entities
entities:
  - label: Batteries
    type: section
filter:
  include:
    - attributes:
        battery_level: <= 100
      options:
        type: 'custom:battery-entity'
    - attributes:
        battery: <= 100
      options:
        type: 'custom:battery-entity'
sort:
  method: name
type: 'custom:auto-entities'
```

## License
This project is under the Apache License 2.0.