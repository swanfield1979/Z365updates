# Z365updates

Publieke updatebestanden voor Z365. De automatische updater van Z365 gebruikt de GitHub Releases van deze repository.

De nieuwste gepubliceerde versie is **0.3.13** (16 oktober 2026).

- [Release 0.3.13 en wijzigingsinformatie](https://github.com/swanfield1979/Z365updates/releases/tag/v0.3.13)
- [Download Z365 0.3.13 voor Windows x64](https://github.com/swanfield1979/Z365updates/releases/download/v0.3.13/Z365-0.3.13-win-x64.zip)
- [SHA256-controlesom](https://github.com/swanfield1979/Z365updates/releases/download/v0.3.13/Z365-0.3.13-win-x64.zip.sha256)

## Eén complete Historie scan in 0.3.13

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

1. Download en pak de ZIP van 0.3.13 uit in een aparte map.
2. Start `Herstel-Z365-update.cmd` vanuit die uitgepakte map en selecteer je bestaande Z365-installatiemap.
3. Start de update opnieuw vanuit je bestaande Z365-installatie.

Het herstel vervangt alleen de updatehelper en maakt hiervan een back-up. De bestaande configuratie en gegevens blijven behouden. De ZIP bevat aanvullende instructies in `docs/update-herstel.md`.

## Repository-opzet

Deze repository bevat alleen publieke update-informatie. Installatiebestanden en controlesommen staan als releasebijlagen op GitHub; de applicatiebroncode en bouwscripts worden in de afzonderlijke Z365-bronrepository beheerd. Daarom heeft deze distributierepository geen eigen `source/`- of `release/`-checkout.
