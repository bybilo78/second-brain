---
name: cron-briefing
description: Use when checking cron runs or preparing incident briefs.
version: 1.0.0
author: probiox
license: Proprietary
metadata:
  hermes:
    tags: [probiox, cron, operations, briefing, monitoring]
---

# Cron-Ergebnisse und Morgenbriefing

## Wann dieser Skill verwendet wird

Verwende ihn beim Prüfen geplanter Cron-Läufe, beim täglichen Protokollieren ihrer Ergebnisse oder beim Erstellen eines Morgenbriefings zu Problemen.

## Zweck und Ablage

Nutze diesen Skill, um die Ergebnisse der probiox-Cron-Jobs zentral zu prüfen, knapp zu protokollieren und bei Problemen ein Morgenbriefing zu erstellen. Cron-Jobs müssen nicht selbst in den Vault schreiben, wenn ihr Ausführungsverlauf die benötigten Status- und Fehlerdaten enthält.

Tagesdateien liegen direkt unter:

`/opt/data/second-brain/project-probiox/operations/cron-results/YYYY-MM-DD.md`

Eine README in diesem Ordner ist nicht erforderlich; dieser Skill definiert die Vorgehensweise.

## Ablauf

1. **Cron-Flotte und Läufe prüfen.** Ermittle zuerst alle Jobs mit `cronjob_manage(action="list")`, danach die letzten Ausführungen mit `hermes cron runs --limit 20` oder einem jobbezogenen Aufruf. Gleiche die Run-Historie mit `last_status`, `last_error` und `last_fire_error` aus der Jobliste ab: `completed` bezeichnet den technischen Run-Status und beweist für sich allein nicht, dass die fachlichen Prüfungen im Job erfolgreich waren. Prüfe Zeitraum, Quelle/Typ des Runs und tatsächlich verfügbare Ausgabe; behaupte nicht, dass vollständige Job-Ausgaben vorliegen, wenn nur Status/Fehler abrufbar sind.
2. **Tagesdatei pflegen.** Verwende das Datum des tatsächlichen Runs. Notiere den Zeitstempel als **Ausführungszeitpunkt** (nicht „Laufzeit“, da der Verlauf keine Dauer belegt), außerdem Jobname, Status und bei Fehlern den tatsächlichen Fehlerhinweis. Lies eine bestehende Datei zuerst ein und ergänze sie, statt frühere Einträge zu überschreiben oder denselben Run doppelt aufzunehmen. Schreibe keine vermuteten Ergebnisse.
3. **Morgenbriefing erstellen.** Fasse nur festgestellte Probleme zusammen: betroffener Job, Zeitpunkt, Status/Fehler und gegebenenfalls nötiger nächster Schritt. Wenn keine Probleme festgestellt wurden, sende kein inhaltsloses Briefing, außer der Nutzer bittet ausdrücklich um eine Statusmeldung.
4. **Lücken kenntlich machen.** Wenn der Ausführungsverlauf für einen Job oder Zeitraum fehlt, benenne die Lücke klar. Erfinde keine Ausgaben und ändere Cron-Jobs nicht stillschweigend, um die Lücke zu umgehen.

## Grenzen und Freigabe

- Ein zentraler Tagesbericht genügt; keine separate Datei pro Joblauf anlegen.
- Erfolgreiche Läufe knapp protokollieren; Fehler ausreichend genau, aber ohne unnötige Wiederholung erfassen.
- Die verbindlichen probiox-Referenzen unter `project-probiox/reference/` sind unveränderlich und dürfen durch diesen Ablauf nicht geändert werden.
- Cron-Zeitpläne, Job-Prompts, Zustellungen und weitere externe oder wesentliche Einstellungen nur nach ausdrücklicher Freigabe ändern.
- Beim Einrichten eines regelmäßigen Morgenbriefings erst Zeit und Zustellweg klären, falls sie nicht festgelegt sind; ein Skill allein erstellt keinen Zeitplan.

## Ergebnisdarstellung

Gib das Briefing immer als kurze Liste aus, nicht als Fließtext. Führe jeden geprüften Cron-Job einzeln mit `OK` oder `NICHT OK` auf; ergänze bei `NICHT OK` knapp den Fehler und nötigen nächsten Schritt. Wenn es keine Probleme gibt, liste die geprüften Jobs jeweils mit `OK` auf. Nenne Datenlücken ausdrücklich und markiere sie als `NICHT OK` oder `UNGEKLÄRT`, statt einen Erfolg zu unterstellen. Trenne bestätigte Fakten von Empfehlungen.