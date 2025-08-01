---
id: create-custom-returners
title: Create Custom Returners
supportedDevices: ['cm4','pro']
---
import CardGrid from "/components/CardGrid";
import DeviceSupportBanner from '@site/src/components/DeviceSupportBanner';

<DeviceSupportBanner supported={frontMatter.supportedDevices} />
---

In this guide we redirect accelerometer data to a file on disk, but the functionality is general,
and the procedure can also be used for OBD data, GPS data and others.

1. Start by creating a custom code module of type *Returner*. Go to **Device** > **Custom Code**:

  ![Create custom returner](/img/cloud/device_management/services/create_custom_returners/create_custom_returner.png) 

  This default returner implementation will append results to a file on disk located at
  `/tmp/returner_data.txt`. But in reality, it's possible to integrate with any storage system here.

2. For the accelerometer service named **acc_manager** register the created custom returner as a
hook so it can be used in worker workflows. Go to **Device** > **Services** > **acc_manager** >
**Hooks** > **Create**:

  ![Register custom returner hook](/img/cloud/device_management/services/create_custom_returners/register_custom_returner_hook.png) 

3. Next, we have to use the registered hook by editing the workflow for the **xyz_logger** worker.
  Go to **Device** > **Services** > **acc_manager** > **Workers** > **xyz_logger**. Here we have
  to change the returner from *cloud* to *my_returner*:

  ![Use custom returner in workflow](/img/cloud/device_management/services/create_custom_returners/use_custom_returner_in_workflow.png) 

When above changes have been successfully synchronised to the device, it will start logging
accelerometer data to the specified file.

When logged onto the device using SSH, it is possible to monitor the data in realtime with the
command:

`tail -f /tmp/returner_data.txt`

