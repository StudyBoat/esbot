### Zusammenfassung Aufgabe

ESBot:

- ist ein Chatbot

- ist eine KI-gestützte Lernplattform für Studierende

- beantwortet Fragen zu Kursinhalten mit kontextbezogenen Erklärungen 

- generiert Übungsaufgaben und Quizze zur Selbstüberprüfung 

- speichert Interaktionen für Verlauf und Lernfortschritt. 

**Ziel**: strukturierter und effizienter Lernprozess

#### Teammitglieder (Gruppe 2):

Armanbir Singh, Dominik Szabó, Kevin Schmidhäusler, Konrad Harnisch-John

##### Implementierung als 3 Layered Architecture + optional KI Einbindung

Wir haben uns für eine Webanwendung entschieden.

**Warum?**

Wir haben bereits Erfahrung in Webanwendungen im Studium gesammelt und möchten diese wieder erfrischen. Alle Mitglieder kennen die Grund-Kenntnisse der Web-Entwicklung. Manche besitzen ebenfalls Erfahrungen mit Next.js, React, Angular und Vue und möchten nun Ihren Wissen erweitern indem Sie sich in den jeweiligen Framework vertiefen oder ein neues Framework anwenden. Alternative wäre eine Android App gewesen, wobei hier nur 2 von 4 Mitglieder Erfahrung gesammelt haben während Ihren Praxissemester. Desweiteren interessierten sich manche Mitglieder besonders für UI Tests mit den jeweiligen Frameworks.

Wir haben vor das Frontend mit TypeScript und React um zu setzen, da dies bereits für 3 der 4 Mitglieder bekannt ist. Alternative wäre auch Angular gewesen, jedoch war das letzte Mitglied selbst nicht zu überzeugt davon, weshalb wir uns nach den Mehrheitsprinzip für React entschieden haben.

Fürs Backend planen wir mit C# und ASP.NET zu arbeiten, da robuste und performante Serverentwicklung möglich ist, in Kombination mit Entity Framework Core für vereinfachten Datenbankzugriff und ORM-Funktionalität. 

**Warum?**

2 der 4 Mitglieder haben sich bereits intensiv mit ASP.NET und C# beschäftigt, auch außerhalb des Studiums. Sie haben viele Backend Projekte in C# und ASP.NET realisiert, Ihre bislang erworbene Ergebnisse und Meinungen diesbezüglich ausgetauscht und waren der Überzeugung, dass dies die bessere Wahl ist. Als Alternativen stand noch SpringBoot, welches beide nicht bevorzugt haben, wegen dessen Komplexität/Aufbau + Java und Ihre schlechten Erfahrungen in vorherigen Projekten. 1 Mitglied war nicht so erfreut über diese Entscheidung, Aufgrund der Abstraktion vom Backend in den vergangenen Projekten (:D), hatte aber leider auch keine bessere Alternativen eingebracht.

Für die Datenbank planen wir PostgreSQL zu nutzen, da diese zuverlässig, leistungsfähig und gut mit .NET integrierbar ist. Es ist möglich, dass wir hierbei noch das Tool Liquibase einbinden, wenn ein Data-First approach benutzt wird. Falls nicht, dann erfolgt die Modellierung der Datenbank automatisch im Backend mithilfe von Entity Framework Core.

Zu guter letzt möchen wir eine KI Integration über Modelle wie Gemini, GPT oder Ollama, um flexible und leistungsstarke Sprachverarbeitung zu ermöglichen. 

Welches Modell genau verwendet wird, ist noch nicht festgesetzt. Tendenz ist es entweder Lokal laufen zu lassen oder Kostenfreie Modelle zu verwenden (Beispiel Gemini 2.5 Lite), da wir das ebenfalls bereits in vorherigen Projekten gemacht haben.

Wir werden mit sehr hoher Wahrscheinlichkeit eine API to API Communication einbauen, sodass wir nur an 1 Backend Anfragen senden. Wir haben diesen Vorgang ein wenig ausdiskutiert als wir über die Integration von Keycloak besprochen haben. Zwar ist unser Ziel aktuell nicht Keycloak zu integrieren, jedoch wäre es für eine vollständige zukünftige App einfacher zu integrieren, wenn wir diesen Kommunikation-Pattern verwenden um den Sicherheitsaspekt abzudecken. 

**Weitere Tools, die wir verwenden möchten:**

Docker zur Containerisierung, um konsistente Entwicklungs- und Laufzeitumgebungen sicherzustellen

GitHub zur Versionsverwaltung und Zusammenarbeit im Team

xUnit als Testframework für Unit Tests im Backend

OpenApi/Swagger zur automatischen API Dokumentation

Postman zur manuellen Testen der API

ESLint um die Code Qualität zu verbessern und generelle Prinzipien zu befolgen + Einheitlichen Code zu schreiben.

Husky (Git Hooks) um pre commit hooks zu haben.

pgAdmin oder DBeaver für das visuelle Arbeiten mit PostgreSQL

React Query für einfachen Zustand Management

#### Verantwortlichen:

Grundsätzlich: Jeder darf überall mithelfen, mitentwickeln, lernen etc.

Jedoch möchten wir klare Verantwortungen haben, weshalb wir "Spezialisten" deklarieren.

Kevin Schmidhäusler -> Frontend

Konrad Harnisch-John -> Backend API

Armanbir Singh -> Datenbank

Dominik Szabó -> KI Integration

Warum diese Aufteilung?

Kevin hat ein sehr feines Auge für ein benutzerfreundliches UI.

Konrad beschäftigt sich intensiv mit C# und kennt unter anderem die neuesten Tipps & Tricks, sowie Packages.

Dominik hatte den Wunsch die KI Integration zu machen.

Armanbir kennt sich sowohl mit EF .NET Core als auch mit Liquibase aus und kann somit unabhängig vom gewählten Approach im Projekt beitragen.

Besonderheiten: Falls nicht der Data-First Approach vewendet wird, dann wird Armanbir Singh für die Integrierung von EF .NET Core und damit der Datenbank Modellierung in C# verantwortlich sein und somit auch im Backend arbeiten.
