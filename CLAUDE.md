# Arbeitsregeln für Claude

## Unvollständige Nachrichten prüfen

Prüfe bei jeder Nachricht des Nutzers zuerst, ob sie ein vollendeter Gedanke ist.
Anzeichen für versehentliches Abschicken mit Enter: Satz bricht mitten im Wort oder
mitten im Satz ab, ein angekündigter Teil fehlt („außerdem…“, „und zwar dass“),
oder die Nachricht ergibt ohne Fortsetzung keinen Sinn.

Bei Verdacht: nicht mit der Arbeit anfangen, sondern sofort mit dem Tool
`AskUserQuestion` nachfragen. Zitiere darin das Ende der Nachricht und biete als
**erste** Option „Ja, so abschicken“ an, damit der Nutzer mit Enter bestätigen kann.
Zweite Option: „Nein, ich schreibe weiter“. Bei „Nein“ auf die Fortsetzung warten.
Bei klar vollständigen Nachrichten nicht nachfragen.

## Modellwahl über Subagents

Wähle das Modell selbst, indem du Aufgaben an den passenden Subagent in
`.claude/agents/` delegierst. Der Nutzer soll das Modell nicht umstellen müssen.

| Aufgabe | Subagent | Modell |
|---|---|---|
| Suchen, Dateien lesen, einfache Fragen, Zusammenfassen | `explorer` | Haiku |
| Normales Coden, Bugfixes mit klarer Ursache, Refactoring, Styling | `implementer` | Sonnet |
| Architektur, schwere Bugs, große Umbauten, Sicherheit, Reviews | `architect` | Opus |

Kurze Rückfragen und Antworten auf einfache Fragen erledigst du direkt ohne Subagent.
Nenne am Ende einer Nachricht kurz, welcher Subagent (und damit welches Modell)
eingesetzt wurde, falls einer eingesetzt wurde.
