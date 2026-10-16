# Z365updates

Publieke updatebestanden voor Z365. De automatische updater van Z365 gebruikt de GitHub Releases van deze repository.

De nieuwste gepubliceerde versie is **0.3.12** (16 oktober 2026).

- [Release 0.3.12 en wijzigingsinformatie](https://github.com/swanfield1979/Z365updates/releases/tag/v0.3.12)
- [Download Z365 0.3.12 voor Windows x64](https://github.com/swanfield1979/Z365updates/releases/download/v0.3.12/Z365-0.3.12-win-x64.zip)
- [SHA256-controlesom](https://github.com/swanfield1979/Z365updates/releases/download/v0.3.12/Z365-0.3.12-win-x64.zip.sha256)

## Historie scan in 0.3.12

Kies **Netwerk > Historie scan**. Deze pagina heeft één vaste selectie: **10 jaar of ouder**. Jongere bestanden worden na de datumcontrole direct overgeslagen en niet in de historiescan-index opgeslagen. Er zijn hier geen andere scanopties.

Onder **Opgeslagen scans** blijven alle scans zichtbaar, ook na herstart. Eerdere netwerk- en historiescans uit 0.3.10 en 0.3.11 zijn terug te vinden. Kies **Bekijk scan > PDF maken** voor uitsluitend bestandsnaam inclusief extensie, volledig pad en laatste wijzigingsdatum, **van nieuw naar oud**.

De Windows-update vanuit 0.3.11 is getest met behoud van een eerder gemaakte historiescan, configuratie en runtimegegevens. Daarna zijn ook een nieuwe scan en PDF-download getest. Bewaarde miniscans blijven hervatbaar en eerdere rapporten veranderen niet door vervolgscans.

Een eerdere gewone inventarisatie zonder opgeslagen bestandslijst kan niet achteraf betrouwbaar worden gereconstrueerd. De historie toont dit expliciet; start daarvoor een nieuwe Historie scan.

## Verbeteringen in 0.3.9

Herstelt herhaalde `Directory handle was closed` / `ERR_DIR_CLOSED`-meldingen na een mislukte mapopening. De scanner verwerkt volgende mappen en kan de ontbrekende map later hervatten. Na bijwerken kun je de netwerkscan hervatten.

De verbeteringen uit 0.3.8 blijven beschikbaar:

Grote netwerkscans worden in kleinere stappen opgeslagen en kunnen na pauzeren of onderbreken worden hervat. De voortgang toont de actuele activiteit, het pad en gelezen bytes. Vastgelopen netwerkbewerkingen krijgen een time-out. De scanbelasting is instelbaar en eerder berekende hashes worden bij ongewijzigde bestanden hergebruikt. Grote groepen dubbele bestanden worden verdeeld over pagina's.

## Bijwerken vanaf 0.3.6 of 0.3.7

De oude updatehelper kan na een geslaagde installatie alsnog terugrollen doordat de afsluitcode van npm niet goed wordt gelezen. Herstel eerst deze helper:

1. Download en pak de ZIP van 0.3.12 uit in een aparte map.
2. Start `Herstel-Z365-update.cmd` vanuit die uitgepakte map en selecteer je bestaande Z365-installatiemap.
3. Start de update opnieuw vanuit je bestaande Z365-installatie.

Het herstel vervangt alleen de updatehelper en maakt hiervan een back-up. De bestaande configuratie en gegevens blijven behouden. De ZIP bevat aanvullende instructies in `docs/update-herstel.md`.

## Repository-opzet

Deze repository bevat alleen publieke update-informatie. Installatiebestanden en controlesommen staan als releasebijlagen op GitHub; de applicatiebroncode en bouwscripts worden in de afzonderlijke Z365-bronrepository beheerd. Daarom heeft deze distributierepository geen eigen `source/`- of `release/`-checkout.
