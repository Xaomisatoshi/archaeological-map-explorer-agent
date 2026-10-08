# Datenzugriff, Bildrechte und technische Grenzen

**Prüfstand: 8. Oktober 2026.** Diese Notiz ist eine technische Prozesshilfe, keine Rechtsberatung. Nutzungsbedingungen, Datenprovider und geltende Rechte vor jedem konkreten Einsatz erneut prüfen.

## Google Maps-Link ist kein Bildzugriff

Google dokumentiert Maps-URLs als plattformübergreifende Links zum Starten von Google Maps und Ausführen von Suchen bzw. Anzeigen von Karten- oder Panoramaansichten. Daraus folgt kein API-Zugriff auf Satellitenpixel und keine Erlaubnis, Bildkacheln automatisiert abzurufen. Diese Vorlage verwendet URLs deshalb als Ortsreferenz, bis ein echter, zulässiger Zugriff nachgewiesen ist.

Ein technischer Abruf erfordert eine eigens eingerichtete und verifizierte Schnittstelle. Beispielsweise benötigen Maps Static API-Aufrufe laut Entwicklerdokumentation einen API-Key und ein aktiviertes Billing-Projekt. Eine solche API ist nicht in dieser Vorlage enthalten. API-Antworten und Nutzungsbedingungen können außerdem Anzeige-, Speicher-, Attributions- und Weiterverwendungsbedingungen haben.

## Veröffentlichung und Bildrechte

- Google Geo Guidelines enthalten Bedingungen für die Nutzung und Attribution von Google Maps-/Earth-Bildern in Publikationen und audiovisuellen Formaten. Je nach Verwendung können zusätzliche Vorgaben oder Genehmigungen für Medien/Entertainment gelten. Projekt, Plattform, Schnitt und konkreter Ausschnitt vor Veröffentlichung anhand der dann aktuellen Richtlinien prüfen.
- Google Earth Studio verlangt Attribution für Google Earth und gegebenenfalls Drittanbieter. Google erklärt, keine Lizenz für Google-Earth-Bilder ohne Attribution anzubieten.
- Attribution nicht entfernen oder abschneiden. Die sichtbaren Anbieterhinweise können Maxar, Airbus, CNES, Copernicus oder andere Rechteinhaber nennen. Screenshot, Export, Bearbeitung und YouTube-Einblendung sind getrennt zu prüfen.
- Technische Abrufbarkeit, eine öffentliche Webkarte oder ein Nutzer-Upload belegen nicht automatisch das Recht, Bilddaten zu speichern, weiterzugeben, zu verändern oder öffentlich zu zeigen.
- Die geprüften EWR-Nutzungsbedingungen für Google Maps Platform nennen Einschränkungen für das Verwenden von Google Maps Content zur Verbesserung von KI-Modellen, einschließlich Training, Test, Validierung oder Fine-Tuning. Ob diese Vertragsbedingungen auf einen konkreten Consumer-Maps-/Earth-Export oder einen anderen Datendienst anwendbar sind, muss separat geprüft werden. Für automatisierte Bildauswertung Quelle, Produktbedingungen und Rechte vorab verifizieren; im Zweifel nicht einsetzen.

## Geeignete Datenwege

1. **Vom Nutzer bereitgestellter Export:** Datei, Quelle, Provider, Aufnahmezeit, Nutzungsrecht und gewünschte Verwendung dokumentieren. Keine Attribution entfernen.
2. **Offene/behördliche Fernerkundungsdaten:** Datensatzbedingungen und Anbieterattribution einzeln dokumentieren. Auflösung, Datum, Band/Produkt und Bearbeitung erfassen.
3. **Google Earth Engine:** Der Data Catalog listet unter anderem Landsat-, Sentinel- und weitere Erdbeobachtungsdaten. Zugang, Nutzungsberechtigung und Bedingungen sind datensatz- und projektspezifisch; die Existenz eines öffentlichen Katalogs bedeutet nicht, dass jede Quelle frei weiterverwendet werden darf. Kein Earth-Engine-Zugriff ist hier eingerichtet.
4. **Google Maps Platform API:** nur nach Konto-/Projektkonfiguration, API-Key, Billing, Rechte- und Policyprüfung. Keine Umgehung durch Kachelscraping.

## Technische Grenzen

- Satellitenbildauflösung unterscheidet sich nach Sensor, Gebiet, Datum und Produkt. Globale Sentinel-2-Daten liegen in ausgewählten sichtbaren/NIR-Bändern typischerweise bei 10 m; das genügt nicht, um kleine Bodenmerkmale sicher zu identifizieren. Kommerzielle/Flugbildprodukte können höher auflösen, benötigen aber eigene Rechte.
- Optische Aufnahmen können durch Wolken, Dunst, Schatten, Saison, Vegetationszustand, Sandbewegung, Bewässerung, Mosaikierung und Bildverbesserung beeinflusst sein.
- Google-Maps-Satellitenansichten können aus Mosaiken verschiedener Zeitpunkte und Anbieter bestehen; ein sichtbarer Standalone-Bildzeitpunkt oder einheitlicher Maßstab darf nicht vorausgesetzt werden.
- Oberflächenmuster belegen weder Datierung noch Funktion. Unterirdische Strukturen werden optisch nicht automatisch sichtbar. Gelände- und Höhendaten, Geophysik, historische Karten und Feldprüfung können nötig sein.
- Koordinaten aus Links können Suchmittelpunkt statt Objektmittelpunkt sein. Koordinatenreferenzsystem und Genauigkeit prüfen; Koordinate und erkannte Bildstruktur nicht gleichsetzen.
- KI-/Bildmodelle können Muster halluzinieren, Kontrast überinterpretieren und natürliche Geometrien menschlich deuten. Deshalb Beobachtung, Interpretation und alternative Hypothesen trennen.

## Pflichtprotokoll vor einem Bildabruf

```text
Quelle/Provider:
Produkt/Datensatz:
Abruf- oder Aufnahmedatum:
Zugriffsmethode und tatsächlich bestätigtes Werkzeug:
Nutzungsbedingungen/Lizenz:
Attribution exakt wie gefordert:
Erlaubte interne Analyse:
Erlaubte Veröffentlichung/Video-Nutzung:
Speicherung/Weitergabe:
Kosten/Kontingent/API-Zugang:
Geprüft am / durch:
Offene Rechtefragen:
```

Wenn wesentliche Punkte fehlen, lautet der Status `blocked_rights_unverified` oder `blocked_no_image_access`. Die Analyse darf nicht als erledigt dargestellt werden.

## Offizielle Referenzen

- Google Maps URLs: <https://developers.google.com/maps/documentation/urls/get-started>
- Maps Static API, Key und Billing: <https://developers.google.com/maps/documentation/maps-static/start>
- Google Geo Guidelines: <https://about.google/brand-resource-center/products-and-services/geo-guidelines/>
- Google Earth Studio Attribution: <https://earth.google.com/studio/docs/attribution/>
- Google Maps/Earth Additional Terms: <https://www.google.com/help/terms_maps/>
- Earth Engine Data Catalog: <https://developers.google.com/earth-engine/datasets/>
- Sentinel-2 Dataset und Auflösung: <https://developers.google.com/earth-engine/datasets/catalog/sentinel-2/>
- Sentinel-1 Dataset: <https://developers.google.com/earth-engine/datasets/catalog/sentinel-1/>

Google Maps Platform EEA Terms wurden ebenfalls zur Policyprüfung herangezogen: <https://cloud.google.com/archive/terms/maps-platform/eea-20250604>. Sie enthalten spezifische Nutzungsbeschränkungen. Die anwendbare Vertragsfassung hängt von Produkt, Konto, Region und Nutzungsdatum ab; die obigen Hinweise ersetzen daher keine Prüfung des konkreten Vorhabens.
