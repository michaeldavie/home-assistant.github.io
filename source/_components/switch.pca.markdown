---
layout: page
title: "ELV PCA 301 Switch"
description: "Instructions on how to integrate ELV PCA 301 switches into Home Assistant."
date: 2019-02-24 18:00
sidebar: true
comments: false
sharing: true
footer: true
logo: elv.png
ha_category: Switch
ha_iot_class: Local Polling
ha_release: 0.95
---

The `pca` switch platform allows you to control the state of your [ELV PCA 301 smart switch](https://www.elv.de/funkschaltsteckdose-fuer-energiekostenmonitor-pca-301.html). You need an 868 MHz interface like the [JeeLink](https://www.digitalsmarties.net/products/jeelink) flashed with the [pca-hex firmware](https://github.com/mhop/fhem-mirror/blob/master/fhem/FHEM/firmware/JeeLink_PCA301.hex).

## {% linkable_title Configuration %}

To use your PCA 301 switch or socket in your installation, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
switch:
  - platform: pca
    device: SERIAL_PORT
```

This platform will add all PCA 301 switches which are in range. You can read the total used energy in KWh and the current power in Watt.

{% configuration %}
device:
  description: "The path to you serial console. Get it via: `ls /dev/tty*`."
  required: true
  type: string
name: 
  description: Default name for the plugs.
  required: false
  type: string
{% endconfiguration %}
