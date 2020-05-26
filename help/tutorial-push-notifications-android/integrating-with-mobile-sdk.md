---
title: Stap 2 - De mobiele SDK integreren
description: In dit deel integreren we de Android-toepassing met de Mobile SDK. Mobiele SDK integreren met de Android-app
feature: Push
topics: Mobile
kt: 4826
doc-type: tutorial
activity: use
team: TM
translation-type: tm+mt
source-git-commit: a2f194821a9ce06272eaed979ee2d8c62cccac2b
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# STAP 2 - Integreren [!UICONTROL Mobile SDK] met Android-toepassing

In dit deel integreren we de [!DNL Android] app met [!UICONTROL Mobile SDK]. Voer de volgende stappen uit om [!UICONTROL mobile SDK] [!DNL Android] de app te integreren:

* Open het *ACSPushTutorial* -project in [!DNL Android Studio]
* Maak een nieuwe Java-klasse met de naam *MainApp* die wordt uitgebreid [!DNL android.app.Application]
* Uw projectstructuur op dit punt zou hieronder moeten kijken

![main-app](assets/android-main-app.PNG)

* Vouw de [!DNL Gradle Scripts] map uit. Dubbelklik op het [!DNL build.gradle] tabblad van de module. Plak de volgende afhankelijkheden in de sectie voor afhankelijkheden van het [!DNL build.gradle] bestand. Het [!DNL build.gradle] bestand moet er hieronder als volgt uitzien

```java{.line-numbers}
implementation 'com.adobe.marketing.mobile:campaign:1.+'
implementation 'com.adobe.marketing.mobile:userprofile:1.+'
implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
```

![modulewrijving](assets/module-build-gradle.PNG)

* Synchroniseer uw [!DNL Android] project door op de knop Nu synchroniseren te klikken om uw project te synchroniseren

## Wijzigen [!DNL AndroidManifest.xml]{#modify-android-manifest}

Open *AndroidManifest.xml* en plak de volgende twee regels na het manifestelement en vóór het toepassingselement. Hierdoor kan uw app communiceren met externe gebruikers

```xml{.line-numbers}
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Kopieer de volgende regel in het toepassingselement[!DNL android:name=".MainApp"]Sla [!DNL AndroidManifest.xml]uw [!DNL AndroidManifest.xml] moet er als volgt uitzien

```xml{.line-numbers}
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.acspushtutorial">
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />

<application
    android:name=".MainApp"
    android:allowBackup="true"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:roundIcon="@mipmap/ic_launcher_round"
    android:supportsRtl="true"
    android:theme="@style/AppTheme">

<activity android:name=".MainActivity">
<intent-filter>
    <action android:name="android.intent.action.MAIN" />
    <category android:name="android.intent.category.LAUNCHER" />
</intent-filter>
</activity>
</application>

</manifest>
```