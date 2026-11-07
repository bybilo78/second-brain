---
name: product-maintenance
description: Für die Pflege von probiox-Produkten und Aufgabenlisten.
version: 1.0.0
author: probiox
license: Proprietary
metadata:
  hermes:
    tags: [probiox, product, maintenance, backlog, quality]
    related_skills: [test-driven-development, requesting-code-review]
---

# Produktpflege

## Wann dieser Skill verwendet wird
Verwende ihn für die laufende Pflege von probiox-Produkten: beim Bewerten von Fehlern und Änderungswünschen, Prüfen der Produktdokumentation, Vorbereiten von Wartungsarbeiten und Beurteilen der Veröffentlichungsbereitschaft.

Die probiox-Vault-Ablage `project-probiox/reference/` enthält verbindliche, unveränderliche Vorgaben aus dem Shop:

- `product-types.md`: kontrollierte Produkttypen. Wähle den passendsten bestehenden Typ und übernimm seine Bezeichnung exakt. Einen neuen Typ nur vorschlagen, wenn keiner passt.
- `eu-responsible-persons.md`: Zuordnung verantwortliche Person in der EU zu Marke/Hersteller. Verwende die bestehende Zuordnung für passende Produkte. Fehlt sie oder ist sie nicht eindeutig, kennzeichne das als offen.
- `approved-copy.md`: freigegebene Textbausteine. Verwende passende Einträge wortgetreu.

**Diese Referenzdateien niemals ändern, ergänzen, umbenennen oder bereinigen.** Sie spiegeln feste Vorgaben aus dem Shop wider und sind ausschließlich zum Nachschlagen und Auswählen da. Wenn ein Wert fehlt, widersprüchlich ist oder nicht passt, halte an und frage den Nutzer; passe die Referenz nicht selbst an.

## Shopify-Produktfelder
Verwende bei der Pflege von Shopify-Produkten folgende Feldgruppen als vereinbarten Umfang:

- **Allgemeine Produktfelder:** Titel, Hersteller, Beschreibung, Barcodes.
- **Produkt-Metafelder:** Highlights (3–5 kurze Zusammenfassungen aus der Produktbeschreibung), Ursprungsland, Verantwortlicher.
- **Kategorie-Metafelder – nur für Kosmetika:** Anwendung, Inhaltsstoffe, Warnhinweise. Verwende diese Kategorie-Metafelder nicht für Produkte, die keine Kosmetika sind.

Diese Liste legt den Umfang der Pflege fest, ist aber keine automatische Erlaubnis, Produktdaten zu ändern. Bewahre die belegten Ausgangsinformationen. Leite Highlights ausschließlich aus der Beschreibung ab und erfinde keine Aussagen oder Produktversprechen. Hole vor wesentlichen oder für Nutzer sichtbaren Produktänderungen die Freigabe des Nutzers ein.

## Lieferantenquellen für Kosmetikdaten
Für die Recherche von **Beschreibung, Anwendungshinweisen, Inhaltsstoffen, Warnhinweisen und Ursprungsland** kommen folgende Lieferanten-Webseiten als Quellen infrage:

- **Cosibella:** https://cosibella-wholesale.com/
- **Qudo Beauty:** https://qudobeauty.com/

Suche jeweils die konkrete Produktseite und prüfe, dass Produkt und Variante eindeutig übereinstimmen. Übernimm nur tatsächlich auf der Produktseite belegte Angaben, halte die Quelle intern zur Nachvollziehbarkeit fest und kennzeichne fehlende oder widersprüchliche Angaben, statt sie zu ergänzen oder zu erraten. Die Nennung eines Lieferanten bedeutet nicht, dass jedes Produkt oder jedes Feld dort verfügbar ist. Wenn mehrere Quellen Angaben liefern, gleiche sie ab und wähle für jedes Feld genau ein bestbelegtes, konsistentes Ergebnis; zeige dem Nutzer keine lieferantenweise Gegenüberstellung, sondern nur die ausgewählten Endangaben.

- **Beschreibung:** Formuliere den ausgewählten, belegten Inhalt eigenständig und natürlich um. Übernimm keine Lieferantenbeschreibung wortgleich. Verändere dabei nicht die belegten Produkteigenschaften und füge keine unbelegten Wirkversprechen hinzu.
- **Inhaltsstoffe:** Ermittle die Inhaltsstoffe ausschließlich aus dem eigens ausgewiesenen Inhaltsstoff-/INCI-Bereich der Lieferantenseite. Leite sie niemals aus der Beschreibung, Wirkstoffwerbung oder Produkt-Highlights ab. Bewahre die INCI-Bezeichnungen und Reihenfolge der Quelle; wenn die vollständige INCI-Liste nicht auslesbar ist, melde das und erfinde oder vervollständige sie nicht.
- **Warnhinweise:** Übernimm konkrete Warnhinweise, wenn die Quelle welche aufführt. Falls nach sorgfältiger Suche keine produktspezifischen Warnhinweise auffindbar sind, verwende genau diesen Standardtext: „Nur zur äußerlichen Anwendung. Außer Reichweite von Kindern aufbewahren. Vor direkter Sonneneinstrahlung und Hitze schützen. Kühl und trocken Lagern. Kontakt mit den Augen vermeiden. Nicht auf verletzte oder geschädigte Haut auftragen. Wenn sie gegen einen der Inhaltsstoffe allergisch sind, darf das Produkt nicht angewendet werden.“

## Arbeitsablauf
1. **Zu pflegendes Produkt ermitteln – immer zuerst.** Kläre eindeutig, welches konkrete Produkt gepflegt werden soll, bevor du Änderungen oder produktbezogene Empfehlungen vorbereitest. Wenn noch nicht klar ist, um welches Produkt es geht, frage nach einem eindeutigen Identifikator, vorzugsweise dem Barcode. Eine Möglichkeit zur Identifikation ist das probiox-MCP-Tool `products_get_by_barcode`: Rufe damit anhand des vom Nutzer angegebenen Barcodes die Produkt-Grunddaten ab und bestätige, welches Produkt gefunden wurde. Erfinde oder errate niemals einen Barcode. Wenn kein Barcode vorliegt oder der Abruf kein eindeutiges Produkt ergibt, bitte um weitere Identifikationsdaten und fahre mit der Produktpflege erst fort, wenn das Zielprodukt eindeutig feststeht.
2. **Referenzen und Kontext prüfen.** Prüfe zuerst die freigegebenen Referenzdaten unter `project-probiox/reference/` und verwende passende bestehende Produkttypen, EU-Verantwortliche und Textbausteine unverändert. Prüfe danach relevante Projektdateien, aktuelle Produktdokumentation und vorhandene Fehler- oder Aufgabenlisten. Behandle sie als maßgebliche Informationsquellen und unterstelle kein undokumentiertes Produktverhalten oder keine undokumentierte Roadmap.
3. **Arbeit einordnen.** Unterscheide Fehler, Verbesserungen der Bedienbarkeit, Funktionswünsche, Dokumentationslücken sowie Betriebs- und Veröffentlichungsthemen. Halte Belege und Auswirkungen für Nutzer fest.
4. **Transparent priorisieren.** Beschreibe Auswirkung, Dringlichkeit, Umfang, Abhängigkeiten und Unsicherheiten. Empfiehl eine Priorität mit kurzer Begründung. Ändere eine offizielle Roadmap oder Aufgabenliste nicht stillschweigend.
5. **Nächsten Schritt definieren.** Formuliere für Umsetzungsarbeiten eine knappe Problemstellung und überprüfbare Abnahmekriterien. Ermittle vor Änderungen die betroffenen Bereiche und Risiken. Nutze bei angefragten Codeänderungen den passenden Entwicklungs- und Test-Skill.
6. **Nur freigegebene Änderungen vornehmen.** Vorschläge dürfen vorbereitet werden; vor wesentlichen Änderungen an Produkt, Roadmap, Veröffentlichung, externen Diensten oder nutzersichtbaren Inhalten muss die Freigabe des Nutzers vorliegen. Prüfe vor dem Aufruf eines MCP-Tools Beschreibung und Schema darauf, ob es Daten nur analysiert oder auch ändert; bei nicht eindeutigem Verhalten und möglicher wesentlicher Änderung erst beim Nutzer nachfragen. Ein Auftrag, ein Tool auszuführen, ist nicht automatisch die Freigabe für eine darin verborgene Datenänderung. Nach externen Änderungen den betroffenen Zustand gezielt zurücklesen und verifizieren. Ohne ausdrückliche Freigabe nichts veröffentlichen oder ausrollen.
7. **SQL- und MCP-Zugriffe sauber trennen.** Für Datenbankabfragen zuerst das Schema mit schreibgeschützten `SELECT`-Abfragen ermitteln; verwende nur bestätigte Tabellen und Spalten, parametriere Nutzereingaben und führe jede neue Abfrage testweise über `system_read_database` aus. Nutze für Daten, die ein dediziertes probiox-MCP-Tool bereitstellt (z. B. Validierungsfehler), dieses Tool statt eine unbekannte DB-Struktur zu erraten. Lege SQL-Dateien bei ausdrücklichem Auftrag im gewünschten Projektpfad ab. Fehlt Schemawissen, frage gezielt nach oder dokumentiere die Abfrage als offen/Entwurf – kommentierte Platzhalter sind keine fertigen SQL-Abfragen und dürfen nicht als erledigte Abfragen dargestellt werden.
8. **Prüfen und dokumentieren.** Führe passende Prüfungen durch und berichte die tatsächlichen Ergebnisse. Aktualisiere Projektdokumentation oder Wartungsprotokolle nur dann, wenn es dafür im Projekt einen etablierten Ablageort gibt. Halte die Ablage für den Shop bewusst einfach: verwende vorhandene Ordner und lege keine zusätzliche Verschachtelung oder Wissensstruktur an, solange ein konkreter Bedarf sie nicht rechtfertigt.

## Ergebnisdarstellung
Bei JSON-Ausgaben (einschließlich Antworten von probiox-MCP-Tools) zeige das Ergebnis als gültiges, pretty-gedrucktes JSON in einem `json`-Codeblock. Parse verschachtelte JSON-Strings und stelle die darin enthaltenen Daten strukturiert dar; gib keine JSON-escaped Zeichenfolgen mit `\\n` oder escaped Anführungszeichen als Ersatz für das eigentliche JSON aus. Bewahre bei der Formatierung alle gelieferten Felder, Einträge, Werte und Datentypen unverändert; kürze oder fasse JSON-Ergebnisse nicht zusammen. Bei Toolfehlern zeige das Fehlerobjekt ebenfalls als pretty-gedrucktes JSON. Bei einem Toolfehler darf ein begrenzter Retry mit identischen Eingaben sinnvoll sein; wenn derselbe Fehler erneut auftritt, nicht weiter unverändert wiederholen, sondern stoppen und den Fehler samt tatsächlich beobachtetem Ergebnis melden. Prüfe Tool-Ausgaben außerdem auf interne Widersprüche (z. B. Summen, die nicht zur verarbeiteten Gesamtzahl passen): Werte nicht selbst ergänzen oder korrigieren, sondern die Abweichung ausdrücklich benennen und, sofern möglich, den Zustand gezielt verifizieren. Fasse eine Bewertung oder Wartungsprüfung mit den relevanten ausgewählten Endergebnissen zusammen. Bei der Recherche von Produktfeldern zeige nur die gewählten Werte, nicht eine lieferantenweise Gegenüberstellung. Führe Quellen bei Bedarf separat zur Nachvollziehbarkeit auf.

- Feststellung und Belege;
- Auswirkungen auf Nutzer oder Produkt;
- empfohlene Priorität und Begründung;
- vorgeschlagene Maßnahme und Abnahmekriterien;
- offene Fragen, Abhängigkeiten oder Risiken.

Unterscheide Empfehlungen klar von bestätigten Tatsachen. Erfinde keine Vorfälle, Kennzahlen, Produkteigenschaften oder Angaben zum Umsetzungsstand.