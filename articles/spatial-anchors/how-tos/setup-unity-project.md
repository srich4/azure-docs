---
title: Install Azure Spatial Anchors for Unity
description: Configure a Unity project to use Azure Spatial Anchors
author: msftradford
manager: MehranAzimi-msft
services: azure-spatial-anchors

ms.author: parkerra
ms.date: 03/30/2021
ms.topic: how-to
ms.service: azure-spatial-anchors
---

# Configuring Azure Spatial Anchors in a Unity project

This guide will show you how to get started with the Azure Spatial Anchors SDK in your Unity project.

## Project requirements

[!INCLUDE [Unity Project Requirements](../../../includes/spatial-anchors-unity-project-requirements.md)]

## Configuring a project

Before including the Azure Spatial Anchors SDK in your Unity project, be sure to install the [required](#project-requirements) packages through the Unity Package Manager.

### Download ASA packages
[!INCLUDE [Download Unity Packages](../../../includes/spatial-anchors-unity-download-packages.md)]

### Import ASA packages
[!INCLUDE [Import Unity Packages](../../../includes/spatial-anchors-unity-import-packages.md)]

### HoloLens only: Configure your Unity project XR settings
When developing MixedReality apps on HoloLens, you need to set the XR configuration in Unity. Please refer to [Setting up your XR configuration - Mixed Reality | Microsoft Docs](https://docs.microsoft.com/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)     and [Choosing a Unity version and XR plugin - Mixed Reality | Microsoft Docs](https://docs.microsoft.com/windows/mixed-reality/develop/unity/choosing-unity-version) for more details.

Azure Spatial Anchors SDK 2.9 or older only support Windows XR plugin (com.unity.xr.windowsmr), and hence Azure Spatial Anchor HoloLens Unity package has an explicit dependency on com.unity.xr.windowsmr package.

Azure Spatial Anchors SDK version 2.10.0 or later support both the Mixed Reality OpenXR plugin ([com.microsoft.mixedreality.openxr](https://dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging?_a=package&feed=Unity-packages&view=overview&package=com.microsoft.mixedreality.openxr&protocolType=Npm)) and the Windows XR plugin  ([com.unity.xr.windowsmr](https://docs.unity3d.com/Manual/com.unity.xr.windowsmr.html)). You need to include either of com.microsoft.mixedreality.openxr or com.unity.xr.windowsmr packages in your project per your choice.

### Android only: Configure the mainTemplate.gradle file

1. Go to **Edit** > **Project Settings** > **Player**.
2. In the **Inspector Panel** for **Player Settings**, select the **Android** icon.
3. Under the **Build** section, check the **Custom Main Gradle Template** checkbox to generate a custom gradle template at `Assets\Plugins\Android\mainTemplate.gradle`.
4. Open your `mainTemplate.gradle` file in a text editor.
5. In the `dependencies` section, paste the following dependencies:

    ```gradle
    implementation('com.squareup.okhttp3:okhttp:[3.11.0]')
    implementation('com.microsoft.appcenter:appcenter-analytics:[1.10.0]')
    ```

When it's all done, your `dependencies` section should look something like this:

[!code-gradle[AzureSpatialAnchorsScript](../../../includes/spatial-anchors-unity-android-gradle-setup.md?range=9-13&highlight=3-4)]

## Next steps

> [!div class="nextstepaction"]
> [How To: Create and locate anchors in Unity](./create-locate-anchors-unity.md)
