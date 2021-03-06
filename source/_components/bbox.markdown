---
layout: page
title: "Bbox"
description: "Instructions on how to integrate Bouygues Bbox routers into Home Assistant."
date: 2016-10-22 01:00
sidebar: true
comments: false
sharing: true
footer: true
logo: bbox.png
ha_category:
  - Network
  - Sensor
  - Presence Detection
ha_release: 0.31
ha_iot_class: Local Polling
redirect_from:
 - /components/sensor.bbox/
 - /components/device_tracker.bbox/
---

The `bbox` platform uses the [Bbox Modem Router](https://fr.wikipedia.org/wiki/Bbox/) from the French Internet provider Bouygues Telecom. Sensors are mainly bandwidth measures.

There is currently support for the following device types within Home Assistant:

- [Presence Detection](#presence-detection)
- [Sensor](#sensor)

<p class='note warning'>
Due to third party limitation, the sensors will only be available if Home Assistant and the Bbox are on the same local area network. You can check this by going to 192.168.1.254 with your web browser.
</p>

## {% linkable_title Presence Detection %}

The `bbox` platform offers presence detection by looking at connected devices to a [Bbox](https://fr.wikipedia.org/wiki/Bbox) based router from [Bouygues](https://www.bouyguestelecom.fr/), which is one of the main Internet provider in France.

Bbox is a generic name for different hardware routers. The platform has been tested with the following devices:

- Sagem F@st 5330b

### {% linkable_title Configuration %}

To use an Bbox router in your installation, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
device_tracker:
  - platform: bbox
```

{% configuration %}
host:
  description: IP address of your Bbox device.
  required: false
  type: string
  default: 192.168.1.254
{% endconfiguration %}


<p class='note warning'>
For now and due to third party limitation, the Bbox must be on the same local network as the Home Assistant installation.
</p>

See the [device tracker integration page](/components/device_tracker/) for instructions how to configure the people to be tracked.

## {% linkable_title Sensor %}

To add Bbox sensors to your installation, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
sensor:
  - platform: bbox
    monitored_variables:
      - down_max_bandwidth
      - up_max_bandwidth
      - current_down_bandwidth
      - current_up_bandwidth
```

{% configuration %}
name:
  description: Name to display in the frontend.
  required: false
  default: Bbox
  type: string
monitored_variables:
  description: Sensors to display in the frontend.
  required: true
  type: list
  keys:
    down_max_bandwidth:
      description: Maximum bandwidth available for download.
    up_max_bandwidth:
      description: Maximum bandwidth available for upload.
    current_down_bandwidth:
      description: Instant measure of the current used bandwidth for download.
    current_up_bandwidth:
      description: Instant measure of the current used bandwidth for upload.
{% endconfiguration %}