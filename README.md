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
| name | string | optional | v0.1 | *friendly_name* | Override the entities friendly name.
| warning | integer | optional | v0.1 | 35 | Sets the level at which the battery icon will be shown as yellow.
| critical | integer | optional | v0.1 | 15 | Sets the level at which the battery icon will be shown as red.



### Example usage

```yaml
- type: custom:battery-entity
  entity: sensor.front_door_lock_battery
```

## License
This project is under the Apache License 2.0.
