---
title: Stap 1 - Een Android-toepassing maken en configureren voor gebruik van Firebase Cloud Messaging
description: In dit deel zullen wij [!DNL Android] Te ontvangen app [!UICONTROL Push notifications] verzonden vanuit Adobe Campaign Standard. Om de pushberichten te ontvangen, moet de app zijn geregistreerd bij Google [!DNL Firebase Cloud Service].
feature: Push
user: Admin
level: Experienced
jira: KT-4825
doc-type: tutorial
activity: use
team: TM
recommendations: noDisplay
exl-id: f087d9f2-cce9-4903-977f-3c5b47522c06
source-git-commit: 0ad82fb0533ed8fc2a85c2a32c7e54deef14d05a
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 3%

---

# Stap 1 - Maken [!DNL Android] Toepassen en configureren voor gebruik [!DNL Firebase Cloud Messaging]

In dit onderdeel maakt u [!DNL Android] Te ontvangen app [!UICONTROL Push notifications] verzonden vanuit Adobe Campaign Standard. Als u pushberichten wilt ontvangen, moet de app zijn geregistreerd bij Google [!DNL Firebase Cloud Service].

1. Aanmelden bij uw [!DNL Firebase] account.

   [!DNL Firebase] is een mobiel Google-platform waarmee u snel hoogwaardige apps kunt ontwikkelen. Als u geen [!DNL Firebase] account, maak er een [van hier](https://firebase.google.com).

2. Starten [!DNL Android Studio]
3. Klik op **[!UICONTROL File]** > **[!UICONTROL New]** > **[!UICONTROL New Project].**
4. Selecteer **[!UICONTROL Empty Activity]** en klik op **[!UICONTROL Next].**

   ![android-project](assets/android-project.PNG)

5. Geef het project een betekenisvolle naam.

   In het kader van deze demo hebben wij ons project aangeduid als *[!DNL ACSPushTutorial]*

   ![android-project-configuration](assets/android-project-configuration.PNG)

6. Accepteer de standaardpakketnamen en klik op **[!DNL Finish]** om uw project te maken.
7. De projectstructuur moet er ongeveer zo uitzien als hieronder opgenomen scherm

   ![android-projectstructuur](assets/android-project-structure.PNG)

8. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Firebase].** (hiermee wordt het project toegevoegd aan [!DNL Firebase])
9. Klik op **[!UICONTROL Set up Firebase Cloud Messaging].**

   ![installatiefirewall](assets/android-project-firebase-messaging.PNG)

10. Klik op **[!UICONTROL Connect to Firebase].**
11. Nadat uw app is verbonden met Firebase, klikt u op **[!UICONTROL Add FCM to your app].**
12. Klik op **[!UICONTROL Accept Changes].**

   Wanneer u FCM aan uw app toevoegt, heeft de wizard uw toestemming nodig om enkele wijzigingen in uw project aan te brengen.

   ![[!DNL add-fcm-to-your-app]](assets/firebase-add-fcm-to-app.PNG)

Als uw app met Firebase is geïntegreerd, ontvangt u een bericht zoals hieronder:

![[!DNL fcm-successfull]](assets/android-firebase-success.PNG)

[Zorg ervoor dat uw project wordt vermeld in [!DNL Firebase &#x200B;]console](https://console.firebase.google.com/)

## Configureren [!UICONTROL Push Channel] Instellingen

1. Aanmelden bij [!DNL Firebase] console
2. Open de **[!UICONTROL ACSPushTutorial]** project.
3. Klik op de knop **tandwielpictogram** en opent u de projectinstellingen

   ![projectinstellingen](assets/firebase-project-settings.PNG)

4. Tab naar de **[!UICONTROL Cloud Messaging]** tab.
5. De serversleutel kopiëren

   ![serversleutel](assets/firebase-server-key.PNG)

6. Aanmelden bij uw Adobe Campaign Standard-exemplaar
7. Klik op **[!UICONTROL Adobe Campaign]** > **[!UICONTROL Administration]** > **[!UICONTROL Channels]** > **[!UICONTROL Mobile App].**
8. Selecteer de juiste **[!UICONTROL Mobile Application Property].**
9. Klik op de knop **[!DNL Android]pictogram** in de **[!UICONTROL Push Channel settings]** sectie.
10. Plak de serversleutel in het veld met de serversleutel.

Als alles goed gaat, zou u een SUCCESS bericht moeten zien.

![push-channel-instellingen](assets/push-channel-settings.PNG)

Samenvattend hebben we een [!DNL Android App] en de [!DNL Android App] with [!DNL Firebase]. We hebben de Mobile App in Adobe Campaign vervolgens verbonden met de [!DNL Android App] door de [!DNL Android] De serversleutel van de app is in op de Mobile-app in Adobe Campaign Standard.
