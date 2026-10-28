# Z365updates

Publieke updatebestanden voor Z365. De automatische updater van Z365 gebruikt de GitHub Releases van deze repository.

De nieuwste gepubliceerde versie is **0.3.16** (28 oktober 2026).

- [Release 0.3.16 en wijzigingsinformatie](https://github.com/swanfield1979/Z365updates/releases/tag/v0.3.16)
- [Download Z365 0.3.16 voor Windows x64](https://github.com/swanfield1979/Z365updates/releases/download/v0.3.16/Z365-0.3.16-win-x64.zip)
- [SHA256-controlesom](https://github.com/swanfield1979/Z365updates/releases/download/v0.3.16/Z365-0.3.16-win-x64.zip.sha256)

## Nieuw in 0.3.16

- Opgeslagen scans hergebruiken in Bestandsanalyse, Bestandsacties en Labelbewaking. Combineer extensie en wijzigingsdatums en verplaats de selectie met actuele broncontrole, SHA-256 en migratiebewijs.
- Lege mappen na een nieuwe controle verwijderen. Niet-lege of onbereikbare mappen worden overgeslagen.
- Alle sites scannen vanuit de SharePoint-beheerinventaris, met siteopslag in GB (GiB), aparte bewaarde scans en fouten per site.
- Tenantkopie met aparte bron- en doelsessies, inhoudscontrole en behoud van de bron. Versiehistorie, rechten en encryptiesleutels worden niet gemigreerd.
- Beheeracties zijn na aanmelden standaard beschikbaar. Microsoft-rechten, PIM en bevestigingen per actie blijven gelden.
- View Site Admin gaat door na een fout; Set Site Admin ondersteunt beveiligingsgroepen en Microsoft 365-groepen.
- Labelbewaking kan dagelijks controleren en ingestelde eigenaren per e-mail attenderen zolang Z365 draait en de brontenant is aangemeld. De termijn begint bij de eerste Z365-waarneming; dit is geen bewezen labeltoekenningsdatum. Z365 verlaagt geen labels automatisch.
- DLP Agents analyseert aangeleverde Purview-auditrecords voor bewezen Copilot-documentgebruik. Dit is geen complete live inventaris van agentkennisbronnen.
- Offline installatie met meegeleverde productieafhankelijkheden. Bijgewerkte afhankelijkheden: de productie-audit meldt nul kwetsbaarheden.

317 tests slagen. De interface is op desktop, tablet en mobiel gecontroleerd. De Windows-updateproef vanuit 0.3.14 slaagt met geblokkeerde npm en behoud van instellingen, complete historiescan en historie-PDF. Microsoft-functies zijn lokaal met testclients gecontroleerd en vereisen nog acceptatie in de klanttenant.

Vanuit **0.3.6 t/m 0.3.14**: pak eerst de nieuwe ZIP in een aparte map uit, start daar **Herstel-Z365-update.cmd** en wijs je bestaande programmamap aan. Werk daarna bij via Instellingen > Updates. Of sluit Z365 en kopieer het volledige pakket inclusief node_modules over de bestaande programmamap, met behoud van .env en runtimegegevens. Vanuit de lokale 0.3.15 is helperherstel niet nodig. Node.js 20.17 of hoger blijft vereist.

[Uitgebreide functies, rechten, installatie en beperkingen](https://github.com/swanfield1979/Z365/blob/main/docs/releases/v0.3.16.md) · [Validatie](https://github.com/swanfield1979/Z365/blob/main/docs/validatie-0.3.16.md)

## Snellere PDF-export in 0.3.14

Grote historiescans verzenden de PDF nu tijdens het maken. Lange paden worden sneller verwerkt en afgeronde pagina’s blijven niet allemaal in het geheugen. Bij een afgebroken download stopt de export. Gecontroleerd met 35.862 fictieve bestanden: circa 8 seconden in de lokale proef, tegenover circa 35 seconden voorheen. Andere machines kunnen afwijken.

Werk bij via **Instellingen > Updates**. Kies daarna opnieuw **Scan PDF** bij de opgeslagen historiescan; opnieuw scannen is niet nodig.

## Eén complete Historie scan sinds 0.3.13

Kies **Netwerk > Historie scan** en **Scan starten / hervatten**. De scan bouwt één totaaloverzicht op over alle ingevoerde locaties. Er worden geen losse scans meer getoond.

Ieder verwerkt bestand wordt direct onthouden, inclusief bestanden die te jong zijn en worden overgeslagen. Bij hervatten krijgen die geen nieuwe datumcontrole. Volledig verwerkte mappen en hun inhoud worden niet opnieuw geopend. Alleen ontbrekende bestanden en onvolledige delen worden hervat, ook na herstart.

**Scan PDF** bevat alle opgeslagen bestanden van **10 jaar of ouder** uit alle locaties, zonder dubbele paden. De PDF bevat uitsluitend bestandsnaam inclusief extensie, volledig pad en laatste wijzigingsdatum, **van nieuw naar oud**. De selectiegrens blijft die van de eerste scanstart. Bestanden die later worden gewijzigd of toegevoegd in een afgeronde map worden niet opnieuw gemeten.

Bestaande historiescanresultaten en bekende afgeronde mappen uit 0.3.12 worden bij de update overgenomen. Oude versies onthielden te jonge bestanden nog niet afzonderlijk; in een toen onvoltooide map kunnen die tijdens de eerste hervatting eenmaal opnieuw worden gecontroleerd. De echte Windows-update vanuit 0.3.12 met behoud van resultaten en de totale PDF is getest; 289 tests slagen.

## Verbeteringen in 0.3.9

Herstelt herhaalde `Directory handle was closed` / `ERR_DIR_CLOSED`-meldingen na een mislukte mapopening. De scanner verwerkt volgende mappen en kan de ontbrekende map later hervatten. Na bijwerken kun je de netwerkscan hervatten.

De verbeteringen uit 0.3.8 blijven beschikbaar:

Grote netwerkscans worden in kleinere stappen opgeslagen en kunnen na pauzeren of onderbreken worden hervat. De voortgang toont de actuele activiteit, het pad en gelezen bytes. Vastgelopen netwerkbewerkingen krijgen een time-out. De scanbelasting is instelbaar en eerder berekende hashes worden bij ongewijzigde bestanden hergebruikt. Grote groepen dubbele bestanden worden verdeeld over pagina's.

## Bijwerken vanaf 0.3.6 of 0.3.7

De oude updatehelper kan na een geslaagde installatie alsnog terugrollen doordat de afsluitcode van npm niet goed wordt gelezen. Herstel eerst deze helper:

1. Download en pak de ZIP van 0.3.14 uit in een aparte map.
2. Start `Herstel-Z365-update.cmd` vanuit die uitgepakte map en selecteer je bestaande Z365-installatiemap.
3. Start de update opnieuw vanuit je bestaande Z365-installatie.

Het herstel vervangt alleen de updatehelper en maakt hiervan een back-up. De bestaande configuratie en gegevens blijven behouden. De ZIP bevat aanvullende instructies in `docs/update-herstel.md`.

## Repository-opzet

Deze repository bevat alleen publieke update-informatie. Installatiebestanden en controlesommen staan als releasebijlagen op GitHub; de applicatiebroncode en bouwscripts worden in de afzonderlijke Z365-bronrepository beheerd. Daarom heeft deze distributierepository geen eigen `source/`- of `release/`-checkout.
