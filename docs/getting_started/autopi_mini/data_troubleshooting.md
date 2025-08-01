---
id: mini-data-troubleshooting
title: Data Troubleshooting
supportedDevices: ['mini']
---

import CardGrid from "/components/CardGrid";
import DeviceSupportBanner from '@site/src/components/DeviceSupportBanner';

<DeviceSupportBanner supported={frontMatter.supportedDevices} />
---

## Why Am I Not Seeing Any Data? 

If you've followed the [Getting Started Guide](/getting_started/autopi_mini/index.md)
and tested your [AutoPi](https://www.autopi.io) TMU CM4 device during a drivebut no data is appearing on 
your [AutoPi](https://www.autopi.io) [Cloud](https://www.autopi.io/software-platform/cloud-management) Dashboard, this guide will help you identify and resolve common issues.

Organized as a checklist, this guide outlines potential causes for missing vehicle
data and offers solutions. It is specifically for the [AutoPi](https://www.autopi.io) [Mini](https://www.autopi.io/hardware/autopi-mini) device. For 
[AutoPi](https://www.autopi.io) TMU CM4, please refer to this [guide](/getting_started/autopi_tmu_cm4/index.md).  

![Dashboard](/img/getting_started/autopi_mini/data_troubleshooting/no_data_dashboard.png)

## Common Causes and Solutions for Data Not Appearing on the [Cloud](https://www.autopi.io/software-platform/cloud-management)  

### 1. Connection Issues 

One common reason for missing data is communication issues within the [AutoPi](https://www.autopi.io) [Mini](https://www.autopi.io/hardware/autopi-mini)
or between [AutoPi](https://www.autopi.io) [Mini](https://www.autopi.io/hardware/autopi-mini) and the [Cloud](https://www.autopi.io/software-platform/cloud-management). The SIM card in your [AutoPi](https://www.autopi.io) [Mini](https://www.autopi.io/hardware/autopi-mini) comes 
pre-installed and should function out of the box. 

When your AutoPi [Mini](https://www.autopi.io/hardware/autopi-mini) is connected to your vehicle's OBD-II port, check the 
status of the two LEDs on the device: 

1. **Navigation LED(closer to the edge of the device):**
    
    This LED indicates the status of the GNSS (Global Navigation Satellite System).
    - **Green and blinking slowly:** The device is receiving a GNSS signal. 
    - **Solid green:** The device is not receiving a GNSS signal. 
    - **Off:** This may indicate the device is either in sleep mode or experiencing an issue. 

2.  **Status LED (farther from the edge of the device):**
    
    This LED reflects the device’s operating status.
    - **Blinking every second:** The device is in normal operating mode. 
    - **Blinking every 2 seconds:** The device is in sleep mode. 
    - **Fast blinking:** Indicates modem activity. 
    - **Off:** This could mean the device is not functioning. 

If either LED is not behaving as expected, it could be a sign of connectivity or 
hardware issues that need attention. Try to disconnect it from the OBD-II port, 
then reconnect it. Wait until both lights are green and blinking.  

![AutoPi Mini LED meaning](/img/getting_started/autopi_mini/data_troubleshooting/mini_light_placements_01.png)

### 2. Logger Creation

Another issue to why you are not seeing data on your [AutoPi](https://www.autopi.io) [Cloud](https://www.autopi.io/software-platform/cloud-management) Dashboard could
be the configuration of the loggers.  

In order to view data on the [AutoPi](https://www.autopi.io) [Cloud](https://www.autopi.io/software-platform/cloud-management) Dashboard, you must ensure that loggers
are set up to collect data from your vehicle. While some loggers are created by 
default, they may not be suitable for your specific vehicle. 

For more detailed instructions on creating loggers for the [Mini](https://www.autopi.io/hardware/autopi-mini), refer to our 
[Logger Guide](/getting_started/autopi_mini/create-mini-loggers).

![Loggers configuration](/img/getting_started/autopi_mini/data_troubleshooting/loggers_configuration.png)

Recommendations for Logger Setup: 
- Use the logger groups OBD-II Standard or System, as these are typically 
  compatible with most vehicles. 
- Once your loggers are set up, check the ‘Change History’ to ensure the 
  changes were applied successfully.

### 3. Configuring Widgets 

Once your loggers are in place, the data should display in widgets on the 
Dashboard under Vehicles > Dashboard. 

![Successful dashboard](/img/getting_started/autopi_mini/data_troubleshooting/successful_data_dashboard.png)

A common reason for seeing "No Data" could also be incorrect widget configuration.
For the widget to display data, it must be linked to the appropriate logger. So, 
if you have added or edited the loggers, you will also need to make the changes 
in the Dashboard’s widgets.  

To edit your widget: 
- Click the three dots in the top right corner of the widget. 
- Ensure the configuration, especially the **Field** section, matches the data being logged. 

![Widget actions](/img/getting_started/autopi_mini/data_troubleshooting/configuration_widget.png)

**Customizing Widget Display:**
- You can choose from various display formats such as graphs, line charts, and gauges.
- Set the widget to show data averages, minimums, or maximums based on your preferences.

After adjusting your widget settings, click **Save**. Then, refresh the widget 
using the circle icon in the top right corner to see if the data appears. 
If the data is now visible, your configuration is correct. If you've just 
createda new logger, it may take another vehicle trip for the device to gather 
the required data.   

Don’t forget to save your dashboard changes by selecting **Widget Actions** > **Save**. 

![Widget actions](/img/getting_started/autopi_mini/data_troubleshooting/widget_action.png)

To add a new widget to your dashboard, go to **Widget Actions** and choose 
**Add Widget**. Remember, a logger must be set up beforehand, or the widget 
won't have any data to display.  

When you're satisfied with your dashboard configuration, save your layout via 
**Widget Actions** to keep your settings for future sessions.  


## 4. No data from your AutoPi mini (EV users)

If your [AutoPi](https://www.autopi.io) [Mini](https://www.autopi.io/hardware/autopi-mini) is not sending data to the cloud and you have an electric vehicle (EV), the issue may be due to the device not being able to autodetect the VIN. Unlike internal combustion engine (ICE) vehicles, some EVs do not support automatic VIN detection, which can prevent the device from reading data properly. To resolve this, follow these steps to adjust the advanced settings for EV compatibility. 

![AutoPi.io - Relocator cable](/img/getting_started/autopi_mini/mini_advanced_settings.png)

Recommended advanced settings for Electric Vehicle:

**Option 1: Adjust OBD Feature, this setting ensures the device correctly communicates with your EV.**

1. Go to: Advanced settings → Obd Settings → Obd Feature.
2. Select: Non-OBD Compliant.
3. Press: Save.

**Option 2: Manually enter your VIN (if not detected automatically).**

1. Go to: Advanced settings → Obd Vin Settings.
2. Set Vin: enter your 17-character VIN (digits and capital letters).
3. Pick Vin Source: select Manual.
4. Press: Save.

**Option 3: Set Ignition detection for EVs to properly detect when your EV is on or off.**
1. Go to: Advanced settings →System -> Ignition Settings.
2. Select: Accelerometer.
3. Press: Save.

After making these adjustments, check the 'Change History' tab to confirm that your settings were applied successfully.



