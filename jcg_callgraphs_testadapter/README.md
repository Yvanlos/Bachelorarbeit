# Java Call Graph (JCG) – Vulnerability Reachability Adapter (Bachelorarbeit)

Dieses Repository archiviert meine Implementierung im Rahmen meiner Bachelorarbeit auf Basis des **Java Call Graph (JCG) Frameworks**. Ziel der Arbeit war die Entwicklung einer statischen Sicherheitsanalyse in **Scala** und **Python**, die potenziell verwundbare Methoden in Java-Anwendungen identifiziert, deren Aufrufer (Callers) rückwärts verfolgt und die Ergebnisse strukturiert zur Weiterverarbeitung bereitstellt.

> **Hinweis zur Ausführung:** Dieses Repository dient als Code- und Architektur-Referenz meiner Bachelorarbeit. Da die Entwicklungsumgebung auf spezifischen älteren Tool- und Java-Versionen basierte, ist das Projekt hier als reines Code-Archiv dokumentiert.

![Systemarchitektur mit hervorgehobener eigener Komponente](./pfad-zu-deinem-markierten-architekturdiagramm.png)

---

## 🎯 Mein Beitrag im Überblick

Während das bestehende JCG-Framework den Test-Korpus und die Basis-Infrastruktur bereitstellt, stammen folgende Komponenten vollständig aus meiner Entwicklung:

* **Statische Reachability-Analyse (`StatischeCallGraphAdapter`):** Konfiguration des **OPAL-Frameworks** zur Erstellung eines RTA-Call-Graphs (`RTACallGraphKey`) und rekursive Rückwärts-Traversierung (`addAllCallers`), um alle direkten und indirekten Aufrufer einer verwundbaren Zielmethode zu ermitteln.
* **Metrik-Aggregation & JSON-Serialisierung:** Berechnung relevanter Betroffenheits-Metriken (betroffene Klassen, Kantenanzahl, erreichbare vs. verwundbare Methoden) und Export über **Play JSON**.
* **Isolierte Test- & Demo-Umgebung (`OpalCallgraphTest`):** Eigenständige Analyse-Applikation zur Verifizierung der OPAL-Einstiegspunkte (`ApplicationEntryPointsFinder`) und des JSON-Exports.
* **Socket-basierter JSON-Empfänger (Python):** Ein TCP-Socket-Server (Port `1337`), der serialisierte Call-Graph-Daten über das Netzwerk empfängt, dekodiert und formatiert als `callgraph.json` persistiert.

---

## 🔍 Code-Walkthrough (Direkteinstieg)

Da das Gesamtprojekt viele bestehende Referenz-Adapter (OPAL, Soot, WALA, Doop) enthält, führen diese Links direkt zu den von mir implementierten Kernkomponenten:

* 📁 **[`jcg_callgraphs_testadapter/`](./jcg_callgraphs_testadapter)** – Hauptmodul meiner Bachelorarbeit.
* 📄 **[`StatischeCallGraphAdapter.scala`](./jcg_callgraphs_testadapter/src/main/scala/jcg_callgraphs_testadapter/StatischeCallGraphAdapter.scala)** – Hauptadapter für die RTA-Call-Graph-Analyse, rekursive Caller-Suche und JSON-Generierung.
* 📄 **[`OpalCallgraphTest.scala`](./jcg_callgraphs_testadapter/src/main/scala/jcg_callgraphs_testadapter/OpalCallgraphTest.scala)** – Eigenständige OPAL-Analyse-Anwendung zum Testen und Validieren der Call-Graph-Ausgabe.
* 📄 **[`receiver.py`](./jcg_callgraphs_testadapter/receiver.py)** – Python-TCP-Server zum Empfangen und Speichern der JSON-Call-Graph-Daten *(Dateinamen ggf. anpassen)*.

---

## 🛠 Eingesetzte Technologien & Konzepte
* **Sprachen:** Scala, Python, Java
* **Frameworks & Bibliotheken:** OPAL (Statische Programmanalyse), Play JSON, Typesafe Config
* **Konzepte:** Call-Graph-Konstruktion (RTA), Backward Reachability Analysis, Vulnerability Detection, Socket-Kommunikation (TCP/IP)
