# Schnittstellen

## Eingabeobjekt

Alle Felder sind optional, außer `request`. Nicht bereitgestellte Informationen bleiben `null` oder `unknown`; der Agent ergänzt sie nicht durch Vermutung.

```json
{
  "request": "Beschreibe und prüfe auffällige lineare Strukturen im Gebiet.",
  "location": {
    "google_maps_url": "https://maps.google.com/?q=29.9792,31.1342",
    "place_name": "Beispielgebiet bei Gizeh",
    "coordinates": {
      "latitude": 29.9792,
      "longitude": 31.1342,
      "crs": "EPSG:4326",
      "precision_m": null
    },
    "area_of_interest": null
  },
  "imagery": [
    {
      "asset_id": "img-001",
      "file_or_accessible_url": "./provided/example.tif",
      "source_provider": "unknown",
      "dataset_or_product": "unknown",
      "acquisition_date": "unknown",
      "resolution_m": null,
      "crs": "unknown",
      "license_or_terms_url": "unknown",
      "attribution_required": "unknown",
      "user_confirms_right_to_analyze": false
    }
  ],
  "constraints": {
    "publish_results": false,
    "sensitive_site_handling": "restricted",
    "allowed_tools": [],
    "requested_output_language": "de"
  }
}
```

`google_maps_url` ist eine Ortsreferenz. `file_or_accessible_url` ist nur dann eine Bildquelle, wenn die Umgebung den Zugriff tatsächlich nachweist und die Nutzungsrechte geklärt sind.

## Werkzeugvertrag

Der Agent darf Funktionen nur nutzen, wenn die Ausführungsumgebung sie bereitstellt. Diese Vorlage installiert keine Werkzeuge.

| Fähigkeit | Benötigter Nachweis | Ohne Nachweis |
|---|---|---|
| Maps-Link prüfen | Linkparser/Browser-Zugriff und protokollierter Zielort; kein automatischer Bildzugriff daraus ableiten | Link als Ortsreferenz behandeln |
| Bild lesen | Sichtbare, lesbare Nutzerdatei oder dokumentierte, erlaubte Daten-API | Analyse stoppen/Datei anfordern |
| GIS-Messung | Verfügbare GIS-/Rasterfunktionen, CRS und Auflösung bekannt | Maße nicht behaupten |
| Zeitvergleich | Mindestens zwei erlaubte Bilder mit Aufnahmezeit und vergleichbarer Georeferenz | Zeitentwicklung offenlassen |
| Webrecherche | Such-/Browserwerkzeug tatsächlich erreichbar; Quellen protokollieren | keine externe Quellenprüfung behaupten |

Mögliche spätere Implementierung: QGIS oder GDAL/Rasterio/GeoPandas für lokale Geodaten; offizielle APIs oder offene Datensätze für Fernerkundung. Auswahl, Einrichtung, Kontingent, Kosten und Rechte sind vor Implementierung separat zu prüfen.

## Ausgabeobjekt

```json
{
  "analysis_id": "AME-YYYYMMDD-001",
  "status": "blocked_no_image_access",
  "scope": {
    "request": "Beschreibe und prüfe auffällige lineare Strukturen im Gebiet.",
    "location_reference": "Maps-Link als Ortsreferenz; nicht als Bild abgerufen",
    "coordinate_system": "EPSG:4326",
    "area_of_interest": null
  },
  "data_used": [],
  "tools_used": [],
  "steps": [
    {"step": "access_check", "result": "not_run", "reason": "Keine Bilddaten verfügbar"}
  ],
  "candidates": [],
  "limitations": ["Der Maps-Link stellt in dieser Umgebung keinen nachgewiesenen Bildzugriff bereit."],
  "handoff": {"recipient": null, "package": null},
  "conclusion": "Mit den vorliegenden Daten wurde keine Bildanalyse durchgeführt."
}
```

Erlaubte `status`-Werte: `complete`, `partial`, `blocked_no_image_access`, `blocked_rights_unverified`, `not_assessable`.

### Kandidat

```json
{
  "candidate_id": "C-01",
  "observation": "Im bereitgestellten Bild ist eine annähernd rechteckige Tonwertgrenze sichtbar.",
  "location": {"coordinates": null, "image_pixel_bbox": [120, 80, 240, 190], "precision_m": null},
  "measurements": [],
  "evidence_refs": ["img-001: crop-01"],
  "alternative_hypotheses": [
    {"hypothesis": "moderne Feldgrenze", "supporting_observations": [], "contradicting_observations": [], "status": "unresolved"},
    {"hypothesis": "natürliche Boden-/Erosionsgrenze", "supporting_observations": [], "contradicting_observations": [], "status": "unresolved"}
  ],
  "ratings": {
    "visual_anomaly": "weak",
    "data_quality": "low",
    "alternative_explanations": "unresolved",
    "archaeological_support": "none_from_image"
  },
  "candidate_status": "needs_more_data",
  "expert_review_questions": []
}
```

`image_pixel_bbox` bezieht sich auf ein identifiziertes Bild. Meterkoordinaten nur in `coordinates` ausgeben, wenn sie aus einer validierten Georeferenz abgeleitet wurden.

## Übergaben

- **Jeremy de Sung** erhält nur den Kandidatenbericht mit Bild-/Datensatzprovenienz, offenen Alternativerklärungen und konkreten historischen Recherchefragen. Er prüft historische Quellen; das ersetzt keine archäologische Begutachtung.
- **GEO-Agent** erhält, falls nötig, bestätigte Bezeichnungen und strukturierte Entitätsfelder. GEO wird nicht für Bildzugriff oder archäologische Validierung eingesetzt.
- **Menschliche Fachprüfung** ist erforderlich, bevor öffentliche Aussagen über Fundort, Alter, Kulturzugehörigkeit oder Entdeckung formuliert werden.
