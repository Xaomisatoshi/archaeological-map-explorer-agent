# Prüfbarer Workflow

Jeder Lauf erhält eine eindeutige `analysis_id`. Die Schritte werden in Reihenfolge protokolliert. Ein Schritt darf als `not_run` markiert werden; er darf nicht stillschweigend als erledigt gelten.

## 1. Eingabe sichern und normalisieren

- Eingabetyp bestimmen: Maps-Link, Ortsname, Koordinaten, Bild/GeoTIFF, Vektorlayer oder Mischform.
- URL unverändert dokumentieren und Koordinaten extrahieren, sofern sichtbar und eindeutig. Links nicht als Bilddaten zählen.
- Koordinatenreihenfolge explizit als `lat, lon` bzw. `lon, lat` angeben; WGS84 nur setzen, wenn Quelle oder Format es stützt.
- Gebiet, Suchfrage und gewünschte Ausgabe festhalten. Bei unklarer Lage nachfragen oder einen begrenzten Status liefern.

## 2. Zugriff und Rechte prüfen

- Quelle, Zugriffsmethode, Nutzungsbedingungen, Lizenz, Attribution, Speicherung und geplante Veröffentlichung dokumentieren.
- Tatsächlich verfügbares Werkzeug nennen und einen echten Abruf-/Dateizugriff bestätigen.
- Bei fehlendem Bildzugriff: `status: blocked_no_image_access`; keine visuellen Befunde erzeugen.
- Bei ungeklärten Rechten: `status: blocked_rights_unverified`; nicht herunterladen, speichern oder veröffentlichen.

## 3. Bild und Metadaten validieren

- Datei lesbar? Datum, Auflösung, Projektion, Maßstab und Herkunft vorhanden?
- Bild vollständig genug und räumlich korrekt ausgerichtet?
- Wolken, Haze, Schatten, saisonale Unterschiede, Kachelmosaik, Schärfung oder Kompressionsartefakte erkennbar?
- Fehlende Daten als Einschränkung festhalten. Keine Pixelgröße oder Objektgröße schätzen, wenn keine Maßstabsgrundlage besteht.

## 4. Neutral beschreiben und Auffälligkeit markieren

- Beobachtungen vor Hypothesen protokollieren.
- Kandidaten mit Kennung (z. B. `C-01`), grober Lage/Geometrie und Bildausschnittreferenz markieren.
- Falls GIS-Funktionen vorhanden sind: Georeferenz, Maßstab, Orientierung, einfache Form-/Abstandsmaße und Overlay dokumentieren. Methode und Parameter festhalten.
- Keine visuelle Markierung als Grabungsstelle oder Fundort etikettieren.

## 5. Alternativen und Vergleichsdaten prüfen

- Für jeden Kandidaten natürliche, moderne und technische Alternativen prüfen.
- Gelände-/Höhenmodell, Hydrographie, Geologie, bekannte heutige Landnutzung oder unabhängige Fernerkundungsdaten nur verwenden, wenn Zugriff, Lizenz und Herkunft dokumentiert sind.
- Zeitvergleiche nur mit Aufnahmezeitpunkten, Auflösung und Registrierungshinweis ausgeben.
- Widersprechende Evidenz ausdrücklich nennen. „Keine Alternative gefunden“ bedeutet nicht „archäologisch“.

## 6. Kandidat priorisieren

Statt eines scheinpräzisen Wahrscheinlichkeitswerts getrennte Bewertungen verwenden:

- `visual_anomaly`: none / weak / moderate / strong
- `data_quality`: low / medium / high
- `alternative_explanations`: plausible / unresolved / few_observed
- `archaeological_support`: not_assessed / none_from_image / external_expert_confirmation

Der Gesamtstatus ist einer aus:

- `not_assessable`
- `no_robust_visual_anomaly`
- `needs_more_data`
- `candidate_for_expert_review`

## 7. Bericht und Übergabe

- JSON gemäß `INTERFACES.md` und eine lesbare Kurzfassung ausgeben.
- Belege mit Bild-/Layer-ID und markierter Stelle verlinken. Rechtekonforme Screenshots oder Visualisierungen separat kennzeichnen.
- An Jeremy de Sung übergeben: Kandidatenbericht, neutrale Beobachtungen, Alternativhypothesen, offene Fragen und Quellenbedarf. Fachhistorische Schlussfolgerungen bleiben dort getrennt.
- An GEO nur übergeben, wenn Bezeichnungen, Entitäten oder strukturierte Inhaltsdarstellung gebraucht werden.
- Exakte sensible Koordinaten nicht in öffentliche Content-Ausgaben übernehmen.

## 8. Qualitäts- und Abbruchprüfung

Vor Abschluss prüfen:

- [ ] Ist Bildzugriff tatsächlich bestätigt oder korrekt als nicht erfolgt markiert?
- [ ] Sind Quelle, Datum, Maßstab/Auflösung und Rechte dokumentiert oder als offen markiert?
- [ ] Sind Beobachtung und Interpretation getrennt?
- [ ] Wurden natürliche, moderne und technische Alternativen erwogen?
- [ ] Ist klar, dass der Agent keine archäologische Entdeckung bestätigt?
- [ ] Ist jede Messung reproduzierbar beschrieben?
- [ ] Sind sensible Koordinaten geschützt?

Fehlt Bildmaterial, Rechtefreigabe oder ein notwendiges Metadatum, wird der Lauf begrenzt oder gestoppt. Eine leere Evidenzlage wird nicht mit plausibler Erzählung gefüllt.
