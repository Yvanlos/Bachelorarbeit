# Java Call Graph (JCG) – Test-Adapter (Bachelorarbeit)

Dieses Repository archiviert meine Implementierung im Rahmen meiner Bachelorarbeit auf Basis des **Java Call Graph (JCG) Frameworks**. Ziel der Arbeit war die Entwicklung und Integration eines neuen Test-Adapters im Modul [`jcg_callgraphs_testadapter`](./jcg_callgraphs_testadapter) zur systematischen Evaluation von Call-Graph-Analysen.

> **Hinweis zur Ausführung:** Dieses Repository dient als Code- und Architektur-Referenz meiner Bachelorarbeit. Da die Entwicklungsumgebung auf spezifischen älteren Tool- und Java-Versionen basierte, ist das Projekt hier als reines Code-Archiv dokumentiert.

---

## 🎯 Mein Beitrag im Überblick

Während das bestehende JCG-Framework den Test-Korpus, das `Shared Model` und die `Matching Evaluation` bereitstellt, wurden folgende Komponenten von mir entwickelt:

* **Schnittstellen-Implementierung (`jcg_callgraphs_testadapter`):** Anbindung einer externen Call-Graph-Quelle an das JCG-Framework.
* **Datenmodell-Transformation:** Übersetzung der spezifischen Call-Graph-Strukturen in das einheitliche `Shared Model` von JCG.
* **Evaluations-Integration:** Vorbereitung der Daten für den Abgleich (Soundness & Precision) gegen die Ground Truth.

---

## 🔍 Code-Walkthrough (Direkteinstieg)

Da das Gesamtprojekt viele bestehende Adapter (OPAL, Soot, WALA, Doop) enthält, führen diese Links direkt zu den von mir geschriebenen Kernkomponenten:

Implemetierungen Links... mit Beschreibung 
---

## 🛠 Eingesetzte Technologien & Konzepte
* **Programmiersprachen:** Scala, Java
* **Konzepte:** Statische Programmanalyse, Call-Graph-Konstruktion, Software-Architektur, Adapter-Pattern
