# MoveScope – KI-gestützte Umzugskostenschätzung

MoveScope ist eine spezialisierte Web-Plattform, die den Prozess der Umzugskostenschätzung digitalisiert. Statt Vor-Ort-Besichtigungen ermöglicht ein geführter Videorundgang durch den Kunden die automatische Erstellung von Inventarlisten, Volumenberechnungen und Problemerkennungen. Das System besteht aus drei eng verzahnten Kernkomponenten, die gemeinsam einen durchgängigen, KI-gestützten Workflow bilden.

## 1. Kunden-App: Geführter Videorundgang

Die Kunden-App ist eine mobile Web-Anwendung, die über einen Link im Browser des Smartphones gestartet wird. Sie ist bewusst reduziert und führt den Kunden Schritt für Schritt durch die Aufnahme.

### Aufnahme-Workflow
1. Geführte Szenenabfolge nach Räumen (Wohnzimmer, Küche, Schlafzimmer usw.).
2. Zusätzliche Nahaufnahmen großer oder schwerer Objekte (z. B. Flügel, große Schränke).
3. Dokumentation von Wegen und Engstellen zwischen Wohnung und Parkplatz (Treppen, Aufzüge, enge Flure).

### Technik
- **WebRTC** für latenzarmes Live-Streaming mit Fallback auf klassischen Upload bei Verbindungsproblemen.
- Zugriff auf Kamera (inkl. Front-/Rückkamera) und Mikrofon über die Browser-APIs.
- Fortschrittsindikatoren und Validierung, damit keine wichtigen Bereiche ausgelassen werden.

## 2. Analyse-Engine: Computer-Vision-gestützte Auswertung

Das Backend verarbeitet eingehende Videos, extrahiert verwertbare Daten und generiert automatisch strukturierte Berichte.

### Verarbeitungspipeline
1. Entgegennahme des Video-Streams und Persistierung.
2. Zerlegung in Frames, Vorverarbeitung (Stabilisierung, Rauschreduktion).
3. Inferenz über trainierte CV-Modelle und Aggregation der Ergebnisse.

### Computer-Vision-Module
- **Objekterkennung:** Identifikation von Möbeln, Geräten und Umzugskartons (z. B. mittels TensorFlow/PyTorch, Transfer Learning, kontinuierliches Nachtrainieren).
- **Volumenabschätzung:** Kombination aus Objektklassifikation, Dimensionsschätzung (z. B. mit Referenzobjekten wie Türen) und Raumsegmentierung zur Ermittlung des Gesamtvolumens in m³/ft³.
- **Problemzonen-Erkennung:** Analyse der Umgebung auf enge Treppenhäuser, fehlende Aufzüge, verwinkelte Wege oder Spezialobjekte wie Tresore.

### Berichtsgenerierung
- Automatische Inventarliste mit Mengen, Varianten und Besonderheiten.
- Zusammenfassung des berechneten Gesamtvolumens.
- Hervorhebung von Risikofaktoren und Warnhinweisen für die Planung des Umzugsteams.

## 3. Dashboard für Umzugsunternehmen

Das Dashboard ist die Schaltzentrale für Disponenten und Vertriebsteams.

### Kernfunktionen
- **Auftragsverwaltung:** Erfassen neuer Aufträge, Versenden des Aufnahme-Links, Statusverfolgung (Neu, Analysiert, Angebot erstellt).
- **Analyse-Ergebnisse:** Einsicht in Inventar, Volumen, Probleme; Wiedergabe der Originalvideos zur Validierung.
- **Kostenvoranschlag-Tool:** Parametrierbare Preislogik (Preis pro m³, Zuschläge für schwere Objekte, Personalaufwand) zur automatischen Angebotserstellung mit ~95 % Genauigkeit.
- **API-Integrationen:** REST-Schnittstelle zum Export der Analysedaten in gängige Branchensoftware (z. B. MoverBase, SmartMoving).
- **Billing & Usage Tracking:** Verbrauchsbasierte oder abonnementsbasierte Abrechnung pro Unternehmen.

## Technische Leitplanken und Herausforderungen
- **Skalierbarkeit:** Microservice-Architektur oder modulare Monolithen mit klar getrennten Verantwortlichkeiten, Cloud-native Bereitstellung (Container, Kubernetes).
- **Datensicherheit & Compliance:** DSGVO-konforme Verarbeitung, Verschlüsselung im Transit und at Rest, Zugriffskontrollen.
- **KI-Modellentwicklung:** Aufbau eines annotierten Datensatzes, kontinuierliche Verbesserung mittels Active Learning, Monitoring von Modell-Drift.
- **Qualitätssicherung:** Automatisierte Tests, Synthetic-Video-Generierung für Regressionstests, manuelle Reviews in frühen Phasen.

## Nächste Schritte
1. **Discovery & Feasibility:** Validierung der Anforderungen mit Pilotkunden, Erstellung eines technischen Proof of Concept für Video-Upload und Basis-Objekterkennung.
2. **MVP-Implementierung:** Aufbau der Aufnahme-App, erste Version der Analyse-Pipeline und Dashboard-MVP für interne Tester.
3. **Skalierung & Integration:** Erweiterung des Objektkatalogs, Feintuning der Volumenberechnung, Aufbau von Partnerintegrationen und Billing.

MoveScope verschiebt den Fokus weg von manueller Datenerfassung hin zu datengestützter Automatisierung. Der größte Entwicklungsaufwand liegt in der Backend- und KI-Architektur, die den Kern der Wettbewerbsvorteile bildet.
