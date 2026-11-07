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

1. **Cron-Flotte und Läufe vollständig abgrenzen.** Ermittle zuerst, welche Hermes-Profile zur angefragten Flotte gehören; `cronjob_manage(action="list")` zeigt nur Jobs des aktiven Profils und ist nicht automatisch eine systemweite Liste. Wenn der Nutzer andere Profile erwähnt oder ein Vollbriefing erwartet, prüfe jedes dafür zugängliche Profil separat, z. B. mit `HERMES_HOME=/opt/data hermes cron list` für das Default-Profil, zusätzlich zum aktiven Profil. Führe anschließend `hermes cron runs --limit 20` jeweils im selben Profilkontext aus und gleiche die Läufe mit `last_status`, `last_error` und `last_fire_error` ab. Nenne die geprüften Profile und kennzeichne nicht zugängliche Profile als Lücke; behaupte nicht, die gesamte Cron-Flotte geprüft zu haben, wenn nur das aktive Profil abgefragt wurde. `completed` bezeichnet den technischen Run-Status und beweist für sich allein nicht, dass fachliche Prüfungen erfolgreich waren. Prüfe Zeitraum, Quelle/Typ des Runs und tatsächlich verfügbare Ausgabe; behaupte nicht, dass vollständige Job-Ausgaben vorliegen, wenn nur Status/Fehler abrufbar sind.
2. **Tagesdatei pflegen.** Verwende das Datum des tatsächlichen Runs. Notiere den Zeitstempel als **Ausführungszeitpunkt** (nicht „Laufzeit“, da der Verlauf keine Dauer belegt), außerdem Jobname, Status und bei Fehlern den tatsächlichen Fehlerhinweis. Lies eine bestehende Datei zuerst ein und ergänze sie, statt frühere Einträge zu überschreiben oder denselben Run doppelt aufzunehmen. Schreibe keine vermuteten Ergebnisse.
3. **Morgenbriefing erstellen.** Fasse nur festgestellte Probleme zusammen: betroffener Job, Zeitpunkt, Status/Fehler und gegebenenfalls nötiger nächster Schritt. Wenn keine Probleme festgestellt wurden, sende kein inhaltsloses Briefing, außer der Nutzer bittet ausdrücklich um eine Statusmeldung.
4. **Lücken kenntlich machen.** Wenn der Ausführungsverlauf für einen Job oder Zeitraum fehlt, benenne die Lücke klar. Erfinde keine Ausgaben und ändere Cron-Jobs nicht stillschweigend, um die Lücke zu umgehen.

## Grenzen und Freigabe

- Ein zentraler Tagesbericht genügt; keine separate Datei pro Joblauf anlegen.
- Erfolgreiche Läufe knapp protokollieren; Fehler ausreichend genau, aber ohne unnötige Wiederholung erfassen.
- Die verbindlichen probiox-Referenzen unter `project-probiox/reference/` sind unveränderlich und dürfen durch diesen Ablauf nicht geändert werden.
- Cron-Zeitpläne, Job-Prompts, Zustellungen und weitere externe oder wesentliche Einstellungen nur nach ausdrücklicher Freigabe ändern.
- Beim Einrichten eines regelmäßigen Morgenbriefings erst Zeit und Zustellweg klären, falls sie nicht festgelegt sind; ein Skill allein erstellt keinen Zeitplan. Vor dem Anlegen immer die Jobs in allen relevanten Profilen prüfen, damit kein bestehender Briefing-Job übersehen und dupliziert wird.

## Ergebnisdarstellung

Gib das Briefing immer als kurze Liste aus, nicht als Fließtext. Führe jeden geprüften Cron-Job einzeln mit `OK` oder `NICHT OK` auf; ergänze bei `NICHT OK` knapp den Fehler und nötigen nächsten Schritt. Wenn es keine Probleme gibt, liste die geprüften Jobs jeweils mit `OK` auf. Nenne Datenlücken ausdrücklich und markiere sie als `NICHT OK` oder `UNGEKLÄRT`, statt einen Erfolg zu unterstellen. Trenne bestätigte Fakten von Empfehlungen.