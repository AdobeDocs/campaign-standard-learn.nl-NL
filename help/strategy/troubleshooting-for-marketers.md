---
title: Problemen oplossen voor marketeers
description: Kennis van de meest voorkomende fouten kan u helpen sneller problemen op te lossen en uw productiviteit te verhogen. Deze het oplossen van problemenuiteinden om u te helpen gelijkaardige fouten effectief oplossen aangezien zij voorkomen.
feature: Workflows
role: User
level: Beginner, Intermediate, Experienced
doc-type: Article
last-substantial-update: 2023-05-18T00:00:00Z
jira: KT-13256
thumbnail: KT-13256.jpeg
exl-id: 24a6815b-52d1-4bd6-9d27-522720a91f83
source-git-commit: 83b1b0c98d74d4555269a7d90051146d21824dc0
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Oplossen van problemen voor marktspelers: 5 algemene workflowfouten en leveringsfouten

Door: [&#x200B; Suraj Patra &#x200B;](https://www.linkedin.com/in/suraj-p-51612053/){target="_blank"} , Hoogste Consultant, Meijer

Als Senior Ingenieur en klantendeskundige op de producten van Adobe Experience Cloud voor de afgelopen vijf jaar, laat ik bedrijfsgebruikers bij [&#x200B; Meijer &#x200B;](https://www.meijer.com/){target="_blank"}  toe, een Amerikaanse supercentenketen die in 1934 wordt gevestigd, om complexe marketing en transactiecampagnes met ACS in werking te stellen. Enkele projecten waaraan ik heb gewerkt, omvatten aangepaste campagnes om aanbiedingen en orderdetails voor verpersoonlijking op te slaan, geïntegreerd met Adobe Audience Manager, en klantinzicht voor segmentopname.


In mijn tijd die ACS gebruikt, heb ik fouten tegengekomen, wat tijdrovend en frustrerend kan zijn om op te lossen. Kennis van de meest voorkomende fouten kan u helpen sneller problemen op te lossen en uw productiviteit te verhogen. Hieronder vindt u de tips voor het oplossen van problemen waarmee u vergelijkbare fouten op effectieve wijze kunt oplossen.

## Fout bij gegevenstype komt niet overeen

**Code van de Fout:**
`PGS-220000 PostgreSQL error: ERROR: operator does not exist: character varying = bigint`

**Oorzaak:**
Deze fouttypen worden in een workflow weergegeven wanneer u probeert het gebruik van velden met verschillende gegevenstypen te combineren. Wanneer u bijvoorbeeld een bestand uploadt met een bestand dat een tekenreeksveld bevat en u probeert het tekenreeksveld te koppelen aan een profielveld dat een gegevenstype int heeft.

![&#x200B; gegeven-type-mismatch-error &#x200B;](/help/assets/kt-13256/data-type-mismatch.png)

**Oplossing:**
Wijzig het gegevenstype van het veld in de activiteit Bestand laden in het gegevenstype dat u wilt gebruiken. Open de activiteit Bestand laden. Ga naar het tabblad &#39;COLUMN DEFINITION&#39; en wijzig het gegevenstype van het gewenste veld.


![&#x200B; gegeven-type-mismatch-oplossing &#x200B;](/help/assets/kt-13256/data-type-mismatch-solution.png)

## Personalization-leveringsfout

**Code van de Fout:**
`The schema for profiles specified in the transition ('') is not compatible with the schema defined in the delivery template ('nms:recipient'). They should be identical.`

**Oorzaak:**
Deze fout treedt op wanneer u een e-mail naar een adres verzendt, maar de e-mail of een andere id niet in overeenstemming is met een profiel. Als u een e-mailbericht wilt verzenden, moet de e-mail of de id altijd zijn gekoppeld aan een profiel.

![&#x200B; werkschema met verzoeningsactiviteit &#x200B;](/help/assets/kt-13256/del-persn-error-wf.png)

**Oplossing:**
Een gemeenschappelijke identiteitskaart moet bestaan van het geladen dossier met de ontvankelijke lijst. Deze algemene sleutel voegt het ladingsdossier aan de ontvankelijke lijst binnen de verzoeningsactiviteit toe. E-mails worden mogelijk niet verzonden naar records die niet bestaan in de tabel met ontvangers. Hiervoor is deze afstemmingsstap binnen de workflow vereist. Hierdoor zou u de activiteit van het inkomende ladingsdossier met een herkenningsteken zoals e-mailidentiteitskaart van het profiel in overeenstemming brengen. Het schema `nms:recipient` verwijst naar de profielentabel en het in overeenstemming brengen van de inkomende verslagen met profiel maakt het beschikbaar tijdens e-mailvoorbereiding.

Raadpleeg de schermafbeelding voor afstemmingsactiviteiten, zoals hieronder wordt weergegeven.

![&#x200B; werkschema met verzoeningsdetail &#x200B;](/help/assets/kt-13256/del-persn-error-wf-solution.png)

Leer meer over [&#x200B; verzoening &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign-standard/using/managing-processes-and-data/data-management-activities/reconciliation).

## Gegevensfout algemeen veld

**Code van de Fout:**
`The document types of inbound events (''and'') are incompatible (step 'Exclusion'). Unable to perform the operation. `

**Oorzaak:**
Deze kwestie komt terwijl het gebruiken van de **uitsluitingsactiviteit** in werkschema ACS voor, wanneer het uitvoeren van een uitsluiting die op identiteitskaart wordt gebaseerd, wanneer de Primaire reeks, en de uitgesloten reeks niet de zelfde gebiedsnamen hebben.


![&#x200B; Gemeenschappelijke Fout van de Dataset van het Gebied &#x200B;](/help/assets/kt-13256/dataset-error.png)

**Oplossing:**

Deze fout kan op twee manieren worden opgelost:

1. Dezelfde veldnaam gebruiken in zowel primaire als uitgesloten velden en dat veld als id gebruiken

   OF

2. Gebruik de methode voor JOINS-uitsluiting om het veld te selecteren waarop u de records wilt uitsluiten.

![&#x200B; Gemeenschappelijke fout van de Dataset van het Gebied - Oplossing &#x200B;](/help/assets/kt-13256/dataset-error-solution.png)

## Fout veldnaam gedropt

**Code van de Fout:**
`XTK-170036 Unable to parse expression 'i__name'`

**Oorzaak:**

De punten van de mislukking kunnen in een **verrijkingsactiviteit** voorkomen. Een van de meest voorkomende wordt hieronder weergegeven.

![&#x200B; Vervallen Fout van de Naam van het Gebied &#x200B;](/help/assets/kt-13256/field-name-dropped-error.png)

Dit gebeurt wanneer u handmatig een expressienaam bewerkt in de activiteit. In de afbeelding ziet u dat de expressie is gewijzigd van `name ` in `i__name` .

**Oplossing:**

U kunt deze fout op drie manieren oplossen:

1. Wijzig de naam weer in de oorspronkelijke expressie.

2. Als u een nieuwe naam wilt gebruiken, verander de waarden in de **verrijkingsactiviteit**.

3. Als je je niet herinnert wat er veranderd is, zou je best de activiteit opnieuw kunnen creëren.

## Fout bij tijdelijk neerzetten van tabel 

**Code van de Fout:**
`XTK-170024 The temporary schema "temp:deliveryEmail1" is not defined in the current context.`

**Oorzaak:**
Dit is een algemene fout in gecompliceerde workflows met verrijking of andere activiteiten. Dit betekent waarschijnlijk dat sommige werkstromen voor activiteit niet correct worden opgeslagen tijdens meerdere wijzigingen in de werkstroom.

![&#x200B; Tijdelijke fout bij neergezette tabel &#x200B;](/help/assets/kt-13256/temp-table-dropped-error.png)

**Oplossing:**
Deze fout kan op vele manieren optreden, dus er is geen eenvoudige oplossing. Als het een eenvoudige werkstroom is, dan zou het beter zijn om de activiteit opnieuw te vormen. In een gecompliceerde workflow is het beter om de workflowactiviteiten naar een nieuwe workflow te kopiëren, deze op te slaan en opnieuw uit te voeren.
