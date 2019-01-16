# Lovelace forked daapd card
A lovelace card for [Home Assistant](https://github.com/home-assistant/home-assistant) to control a forked daapd instance.

This card allow you to control your forked daapd instance through Home Assistant.
The following controls are available: `master volume`, `play/pause`, `next/previous`, `on/off`, `output selection`, `individual output volume`.

<img src="https://user-images.githubusercontent.com/457678/46584235-03d92100-ca61-11e8-9d4d-969cbca7f88c.gif" alt="Preview" width="400">

## Requirements
- Forked daapd built with websocket support.
- Forked daapd setup as an media_player (mpd component) in Home Assistant

## Install

### Simple install

- Copy `forked-daapd-card.js` into your `config/www` ”folder.
- Add a reference to the `forked-daapd-card.js` inside your `ui-lovelace.yaml`.

```yaml
resources:
  - url: /local/forked-daapd-card.js?v=0.0.2
    type: module
```

### Install using git

- Clone this repository into your `config/www` folder using git.

```bash
git clone https://github.com/kalkih/forked-daapd-card.git
```

- Add a reference to the card in your `ui-lovelace.yaml`.

```yaml
resources:
  - url: /local/forked-daapd-card/forked-daapd-card.js?v=0.0.2
    type: module
```

## Updating

- Locate your `forked-daapd-card.js` in `config/www` or wherever you ended up storing it.
- Replace it with the latest version of [forked-daapd-card.js](forked-daapd-card.js).
- Add the new version number to the end of the cards reference url in your `ui-lovelace.yaml` like below.

```yaml
resources:
  - url: /local/forked-daapd-card.js?v=0.0.2
    type: module
```

If you went the `git clone` route, just run `git pull` from inside your `config/www/forked-daapd-card/` directory, to get the latest version of the code. Then add the new version number to the end of the card reference url in your `ui-lovelace.yaml` like below.

```yaml
resources:
  - url: /local/forked-daapd-card/forked-daapd-card.js?v=0.0.2
    type: module
```

## Using the card

### Options

| Name | Type | Default | Since | Description |
|------|:----:|:-------:|:-----:|-------------|
| type | string | **required** | v0.0.1 | `custom:forked-daapd-card`.
| entity | string | **required** | v0.0.1 | The entity_id of your forked-daapd media_player (mpd) in home  assistant.
| ip | string | **required** | v0.0.1 | Set the IP address of your forked-daapd server.
| port | number | 3689 | v0.0.1 | Set the port of your forked-daapd server.
| ws_port | number | 3688 | v0.0.1 | Set the websocket port of your forked-daapd server.
| name | string | optional | v0.0.1 | Set a custom `friendly_name` which is displayed beside the icon.
| icon | string | optional | v0.0.1 | set a custom icon from any of the available mdi icons.
| outputs | list | optional | v0.0.1 | If you want to only show specific outputs, include the id of each one in the list.

- You can find the outputs ids by accessing `http://<forked-daapd-ip>:<port>/api/outputs`

### Example usage

#### Normal
```yaml
- type: "custom:forked-daapd-card"
  entity: media_player.multiroom_audio
  ip: "192.168.1.5"
  name: Multiroom
```

#### Show only specified outputs
```yaml
- type: "custom:forked-daapd-card"
  entity: media_player.multiroom_audio
  ip: "192.168.1.5"
  name: Multiroom
  outputs:
    - "225176710053082"
    - "962995053492"
    - "24918234768"
```

## Getting errors?
Make sure you have `javascript_version: latest` in your `configuration.yaml` under `frontend:`.

Make sure you have the latest versions of `forked-daapd-card.js`.

If you have issues after updating the card, try clearing your browser cache.

## License
This project is under the MIT license.
