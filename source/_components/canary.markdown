---
layout: page
title: "Canary"
description: "Instructions on how to integrate your Canary devices into Home Assistant."
date: 2017-12-07 22:00
sidebar: true
comments: false
sharing: true
footer: true
logo: canary.png
ha_category:
  - Alarm
  - Camera
  - Sensor
ha_release: "0.60"
ha_iot_class: Cloud Polling
redirect_from:
  - /components/alarm_control_panel.canary/
  - /components/camera.canary/
  - /components/sensor.canary/
---

The `canary` integration allows you to integrate your [Canary](https://canary.is) devices in Home Assistant.

There is currently support for the following device types within Home Assistant:

- Alarm
- [Camera](#camera)
- [Sensor](#sensor)

## {% linkable_title Configuration %}

You will need your Canary login information (username, usually your email address, and password) to use this module.

To set it up, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
canary:
  username: YOUR_USERNAME
  password: YOUR_PASSWORD
```

{% configuration %}
username:
  description: The username for accessing your Canary account.
  required: true
  type: string
password:
  description: The password for accessing your Canary account.
  required: true
  type: string
timeout:
  description: Timeout to wait for connections.
  required: false
  type: integer
  default: 10
{% endconfiguration %}

Once loaded, your front end will have the following components:

- A camera image triggered by motion for each camera.
- An alarm control panel for each location.
- A sensor per camera that reports temperature.
- A sensor per camera that reports humidity.
- A sensor per camera that reports air quality.

## {% linkable_title Camera %}

The `canary` camera platform allows you to watch the live stream of your [Canary](https://canary.is) camera in Home Assistant. This requires the [`ffmpeg` component](/components/ffmpeg/) to be already configured.

Once you have [Canary component](/components/canary/) setup, your [Canary](https://canary.is) camera(s) should show up automatically.

## {% linkable_title Configuration %}

You can add the following to your `configuration.yaml` file to configure `canary` camera with optional settings:

```yaml
camera:
  - platform: canary
```

{% configuration %}
ffmpeg_arguments:
  description: Extra options to pass to `ffmpeg`, e.g., image quality or video filter options. More details in [FFmpeg component](/components/ffmpeg).
  required: false
  type: string
{% endconfiguration %}

## {% linkable_title Sensor %}

The `canary` sensor platform allows you to integrate the sensors of your [Canary](https://canary.is) devices in Home Assistant.

To add `canary` sensors to your installation, follow instructions above.

Once loaded, you will see following sensors:

- A sensor per camera that reports temperature.
- A sensor per camera that reports humidity.
- A sensor per camera that reports air quality.
