---
title: Stap 3 - Extensies registreren voor uw mobiele app
description: In dit deel voegen we de code toe om de extensies Gebruikersprofiel, Identiteit, Levenscyclus en Signaal te registreren.
feature: Push
user: Admin
level: Experienced
jira: KT-4827
doc-type: tutorial
activity: use
team: TM
exl-id: d8c0d8c6-2e04-4c27-b27a-d0de79dd953b
source-git-commit: 9be31e056800b806c49a2c5ffbf9f9f42b001d4c
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 13%

---

# Stap 3 - Extensies registreren voor uw mobiele app

In dit deel, voegen wij de code toe om de uitbreidingen van het Profiel van de Gebruiker, van de Identiteit, van de Levenscyclus, en van het Signaal te registreren. We moeten ook de Adobe Campaign Standard-extensie registreren, zoals in de onderstaande code wordt getoond.

Open uw project in [!DNL Android] studio. De gehele code in MainApp verwijderen **behalve de eerste regel die de pakketinstructie is**.

Plak de volgende code in MainApp

<!--
Removed `{.line-numbers}` below
-->

```java
import [!DNL android].app.Application;
import android.util.Log;

import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.Campaign;
import com.adobe.marketing.mobile.Identity;
import com.adobe.marketing.mobile.InvalidInitException;
import com.adobe.marketing.mobile.Lifecycle;
import com.adobe.marketing.mobile.LoggingMode;
import com.adobe.marketing.mobile.MobileCore;
import com.adobe.marketing.mobile.Signal;
import com.adobe.marketing.mobile.UserProfile;

public class MainApp extends Application {

@Override
public void onCreate() {
super.onCreate();

MobileCore.setApplication(this);
MobileCore.setLogLevel(LoggingMode.DEBUG);

try{
    Campaign.registerExtension();
    UserProfile.registerExtension();
    Identity.registerExtension();
    Lifecycle.registerExtension();
    Signal.registerExtension();
    MobileCore.start(new AdobeCallback () {
        @Override
        public void call(Object o) {
            MobileCore.configureWithAppID("copy your launch property id here");
        }
    });
} catch (InvalidInitException e) {
    Log.d("ACS Exception", "exception");
}
}
}
```

Regel 32 u moet uw verstrekken[!UICONTROL &#x200B; Launch] Omgevingsbestand-id van eigenschap. Dit is toegankelijk via de [!UICONTROL environment tab] van uw [!UICONTROL Launch] eigenschap.

![launch-id](assets/launch-id-property.PNG)
