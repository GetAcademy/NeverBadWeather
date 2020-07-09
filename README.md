# Case-oppgave for GET IT-studentenes inneuke i august 2020

M�let med denne uken er � studere og forst� en eksempel-applikasjon som Terje har laget. 
Det er krevende � sette seg inn i eksisterende kode, men det er ogs� veldig l�rerikt!

Applikasjonen dere skal jobbe med er basert p� en id� som Christoffer Hellenes hadde; han
�nsket en app som foresl�r hva han skal ha p� seg ut fra v�rmeldingen.

Terje er tilgjengelig mandag og fredag, men dagene i mellom er tanken at dere jobber selvstendig og individuelt med dette; samtidig som dere hjelper hverandre og deler kunnskapen dere har og f�r. 

Vurder alltid om oppgaven du ser p� gir utbytte for deg. Om den er for lett eller for vanskelig, er det bedre � velge noe annet. Overordnet er ideen � sette seg inn i denne applikasjonen og l�re av det. En m�te � f� til det p� er ved � gj�re sm� endringer. I tillegg til det som er under, kan dere finner p� sm� endringer � gj�re selv - om forslagene under ikke passer.

## Oppgaver

1. Last ned og test applikasjonen. 
   1. Last ned fra [github.com/GetAcademy/NeverBadWeather](https://github.com/GetAcademy/NeverBadWeather). 
   1. Lag en lokal database.
   1. Kj�r skriptet **CreateDb.sql** som du finner i prosjektet **NeverBadWeather.Infrastructure.DataAccess**.
   1. Pass p� at connection stringen i **appsettings.json** peker p� _din_ database.
   1. Kj�r applikasjonen og utforsk hva den gj�r. 
1. Bruk det � tegne opp sekvensdiagrammer til � visualisere logikken i denne applikasjonen. 
    1. Bruk [www.websequencediagrams.com](https://www.websequencediagrams.com/) til � lage et sekvensdiagram av metoden `GetClothingRecommendation()` i `ClothingRecommendationService`.
1. Bruk unit testing til � forst� hva som skjer i **DomainModel** i **Core**. Husk at om du lurer p� hvordan klassen og metoden du tester skal brukes, s� finnes svaret i eksisterende kode. Du kan ogs� kj�re applikasjonen i debug-modus og steppe deg gjennom koden for � forst� hva som skjer. 
    1. En enkel klasse � begynne med er **Location**. Det finnes alt en unit test av denne, som tester at metoden `IsWithin()` returnerer `true` n�r den skal. Lag en ny test som sjekker at den ogs� returnerer `false` n�r den skal, samt tilsvarende tester for de andre metodene i klassen. 
    1. Lag unit tester for en eller flere av disse klassene: 
       -  `PlaceList`
       -  `WeatherForecast` 
       -  `TemperatureStatistics`
       -  `ClothingRule`
1. Bruk unit testing til � forst� hva som skjer i **ApplicationServices** i **Core**. 
   1. En relativt enkel oppgave er � unit teste `CreateOrUpdateRule()`  i `ClothingRecommendationService`. Den skal oppdatere hvis regelen finnes fra f�r, og opprette regelen ellers. Dette kan du unit teste med enkel mocking. 
   1. Hovedlogikken i hele applikasjonen er i metoden `GetClothingRecommendation()` i `ClothingRecommendationService`. Det finnes allerede en unit test av denne, ferdig med mocking. Denne tester et "happy case", dvs. at alt g�r bra. Bruk unit testing til � finne feil og problemer i koden. Pr�v � finne ut hvilke "grensetilfeller" som finnes, dvs. at alt ikke er som det skal. Noen ideer er under, men pr�v � tenke selv, hva som kan v�re "s�rtilfeller" i alle inputene:
        - en ugyldig posisjon
        - en posisjon veldig langt unna
        - et tidspunkt det ikke finnes v�rmelding for
        - hva om ingen regler matcher gitt temperatur
1. Det er mye funksjonalitet som mangler. Ta tak i noe du ser behovet for og som du tror du kan f� til. Under er noen ideer, men tenk gjerne ut noe selv!
    - Ta hensyn til regn. (Det er delvis lagt opp til dette.) Hvordan f�r man det fra Yr? Hvordan m� koden endres for � matche opp reglene ogs� ut fra regn? 
    - La brukeren velge sted istedenfor bare � gi anbefaling ut fra hvor hen er n�:
      - Enten la brukeren velge region, s� by, og s� sted.
      - Eller ha et tekstfelt hvor man skriver inn og f�r et s�keresultat. Et lite tips: Om man har en `oninput` p� tekstfeltet i HTML, og s� tegner opp hver gang teksten endres, s� kan det v�re lurt, for brukeropplevelsen, � sette fokus ([www.w3schools.com/jsref/met_html_focus.asp](https://www.w3schools.com/jsref/met_html_focus.asp)) til tekstfeltet etter at det er tegnet opp p� nytt - slik at man kan fortsette � skrive flere bokstaver i stedsnavnet uten � m�tte klikke i feltet p� nytt. 