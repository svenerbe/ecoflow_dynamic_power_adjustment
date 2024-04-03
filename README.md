# EcoFlow Device API Integration for Power Stream Control

# Overview
This service script facilitates interaction with the EcoFlow device API to manage power streams, specifically targeting sensors on EcoFlow devices. It includes functions for querying device status, adjusting power stream settings, and handling authentication with the EcoFlow API.

# Key Features
Power Stream Control: Allows users to adjust power stream settings for EcoFlow devices, specifically targeting the WN511_SET_PERMANENT_WATTS_PACK command to set power stream values based on TotalPower.

Device Status Check: Enables checking the online status of a specified EcoFlow device, providing feedback on whether the device is online or offline.

Authentication: Handles authentication with the EcoFlow API using access and secret keys, ensuring secure communication with the EcoFlow platform.

# Prerequisites
Pyscript Integration: To get started, you'll first need to install Pyscript: Python scripting integration, available at [Pyscript GitHub Repository](https://github.com/custom-components/pyscript). This integration enables the execution of Python scripts within Home Assistant, facilitating advanced automation tasks and interactions with external APIs.

EcoFlow Access Credentials: Additionally, you'll require the EcoFlow AccessKey and SecretKey, obtainable through a request at [EcoFlow Developer Portal](https://developer-eu.ecoflow.com/). These credentials are necessary for authenticating API requests with the EcoFlow platform.

# Installation
After installation of Pyscript integration pls install the set_ef_powerstream_custom_load_power.py in your pyscript directory. This directory is located in your Home Assitant Home Directory.

# Usage
Set Power Stream: Call the set_ef_powerstream_custom_load_power function with parameters SerialNumber, TotalPower, and optional parameter Automation to adjust the power stream settings for the specified EcoFlow device.

Check Device Status: Utilize the check_if_device_is_online function to determine the online status of a specified EcoFlow device, providing the Serial Number as input.

You can call the Service in your Automation.

## Sample:
```
service: pyscript.set_ef_powerstream_custom_load_power
data:
  SerialNumber: Your Serial Nr.
  TotalPower: "{{ states('sensor.your sensor') | round }}"
  Automation: true
```

# Dependencies
Python Libraries: Utilizes standard Python libraries such as requests, hashlib, hmac, random, time, binascii, and json for handling API requests, authentication, and data manipulation.
Configuration
Access Key and Secret Key: Users must replace placeholders with valid EcoFlow access and secret keys to authenticate API requests.
Limitations
Power Stream Range: The service enforces a limit of 0 to 600 for power stream values, ensuring compatibility with EcoFlow device specifications.

Error Handling: While the script includes error handling, further refinement may be necessary to cover all potential edge cases and exceptions.

This service script provides a convenient way to integrate EcoFlow device control within Home Assistant, enabling users to manage power streams and monitor device status seamlessly.

# Debuging
You can enable debugging for pyscript in your automation.yaml like this:
```
logger:
  default: info
  logs:
    custom_components.pyscript: debug
```
