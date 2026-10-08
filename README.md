# Archaeological Map Explorer (Arbeitsname)

**Status: Entwurf zur Prüfung.** Dieses Repository enthält die Spezifikation für einen eigenständigen Analyseagenten für algorithmische Kartenerkundung und archäologische Bildanalyse. Der Agent wurde noch nicht in ChatGPT eingerichtet und verfügt über keine bestätigte Karten- oder Bildintegration.

## Auftrag

Der Agent findet und dokumentiert auffällige Landschaftsmuster in rechtmäßig zugänglichen Karten- und Fernerkundungsdaten. Er prüft natürliche und moderne Erklärungen und erstellt eine überprüfbare Kandidatennotiz für eine historische Fachprüfung.

Er meldet **Bildauffälligkeiten und Prüfkandidaten**, keine archäologischen Entdeckungen. Eine archäologische Einordnung bleibt qualifizierten Fachleuten und belastbarer Feld- oder Quellenprüfung vorbehalten.

## Abgrenzung zu bestehenden Rollen

- **GEO-Agent**: Entity-Klarheit, KI-Lesbarkeit und strukturierte Inhaltsanalyse ([README](https://github.com/Xaomisatoshi/geo-agent/blob/main/README.md)).
- **Jeremy de Sung**: historische Quellenprüfung und nachvollziehbare Forschungsberichte ([WORKFLOW](https://github.com/Xaomisatoshi/jeremy-de-sung-oracle-bone-research/blob/main/WORKFLOW.md)).
- **Archaeological Map Explorer**: georeferenzierte Bild- und Landschaftsmuster auffinden, visuelle Evidenz dokumentieren, Alternativerklärungen vergleichen und Prüfkandidaten übergeben.

Die GitHub-Prüfung vom 8. Oktober 2026 umfasste 56 für das verbundene Konto zugängliche Repositories. Darunter war keines mit Satellitenbildanalyse, Kartenerkundung oder Archäologie im Namen. Das belegt keine Abwesenheit entsprechender Workspace-Agenten.

## Dateien

- [`SYSTEM_PROMPT.md`](SYSTEM_PROMPT.md): Rolle, Grenzen und Antwortregeln
- [`WORKFLOW.md`](WORKFLOW.md): reproduzierbare Analyseschritte und Qualitätskontrolle
- [`INTERFACES.md`](INTERFACES.md): Eingaben, JSON-Schema, Ausgaben und Übergaben
- [`TEST_CASES.md`](TEST_CASES.md): konkrete Tests einschließlich erwarteter Abbruch- und Übergabezustände
- [`DATA_ACCESS_RIGHTS.md`](DATA_ACCESS_RIGHTS.md): Zugriffsmodell, Rechteprüfung und technische Grenzen

## Benutzung im aktuellen Entwurfsstand

1. Eine Person liefert einen Maps-Link, Koordinaten, einen Bildausschnitt oder einen lizenzierten Fernerkundungsdatensatz.
2. Der Agent prüft, welche Daten tatsächlich vorliegen und ob sie analysiert werden dürfen.
3. Ohne Bilddaten meldet er nur, dass der Ort referenziert wurde, und fordert einen nutzbaren Bildausschnitt oder eine Datenquelle an.
4. Mit Bilddaten erstellt er einen Befundbericht gemäß `INTERFACES.md` und `WORKFLOW.md`.

Ein Link allein öffnet dem Agenten keine Google-Maps-Karte und stellt keine Bild-API dar. Diese Vorlage enthält weder Zugangsdaten noch eine implementierte Kartenintegration. Verfügbare Werkzeuge müssen vor jedem Einsatz explizit eingerichtet und getestet werden.

## Review-Check

- [ ] Agentenname, Mandat und Grenzen freigegeben
- [ ] Zielumgebung und tatsächlich verfügbare Bild-/GIS-Werkzeuge verifiziert
- [ ] Rechte und Quellenregeln für jeden Datentyp geprüft
- [ ] Testfälle mit zugelassenen Beispielbildern ausgeführt
- [ ] Übergabeformat mit GEO und Jeremy abgestimmt
- [ ] Vor einer Einrichtung des Agenten in ChatGPT separate Owner-Freigabe einholen

## Quellen

Offizielle Quellen und Prüfdatum stehen in [`DATA_ACCESS_RIGHTS.md`](DATA_ACCESS_RIGHTS.md). Links und Nutzungsbedingungen können sich ändern; vor Veröffentlichung erneut prüfen.

