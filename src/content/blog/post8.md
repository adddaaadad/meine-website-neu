---
title: "📄 Automatisierte Lebenslaufanalyse mit n8n, Google Gemini & Google Docs"
description: "Wie ich einen smarten Resume-Bot gebaut habe, der PDFs analysiert und direkt als Report in Google Docs ausliefert – mit Fokus auf Datenschutz, Klarheit und Open-Source."
pubDate: "2025-06-21"
heroImage: "/resume-analyzer-bot.webp"
---

## Einleitung

Im Zeitalter von KI-gestützter Bewerbungsauswahl habe ich ein praktisches Tool entwickelt:  
Einen **intelligenten Lebenslauf-Bot**, der hochgeladene Lebensläufe automatisch analysiert –  
Stärken & Schwächen erkennt und einen professionellen Analysebericht erstellt – direkt in **Google Docs**.  
Das Ganze basiert auf **n8n**, **Google Gemini**, **einer PDF-Upload-Funktion** und **Docs-Automation**.

---

## 🔧 Die Idee hinter dem Projekt

Ich wollte ein System schaffen, das:

- **automatisch Lebensläufe auswertet**  
- **konkrete Verbesserungsvorschläge gibt**  
- **das Ganze strukturiert in ein Google Doc schreibt**  
- und **ohne Drittanbieter-Frontend auskommt**

**Datensparsamkeit und Eigenkontrolle** standen dabei im Fokus – keine Cloudplattformen ohne Einblick.

---

## 🧩 Die eingesetzten Technologien

### 🔄 n8n – Die Schaltzentrale

- Open-Source-Workflow-Automatisierung  
- Lokal gehostet auf dem eigenen Server  
- Steuerung aller Schritte: Upload → Analyse → Google Docs  

> Vorteil: Keine sensiblen Daten wandern unkontrolliert in Drittanbieter-Clouds.

---

### 📤 PDF-Upload via Formular

- Eingebautes Webformular in n8n  
- Upload von PDF-Lebensläufen durch Nutzer:innen  
- Startpunkt für den gesamten Analyseprozess

---

### 📑 PDF Extraction – Der Textextraktor

- Extrahiert Inhalte aus der PDF  
- Übergibt strukturierten Text an die KI-Analyse  
- Auch bei ungewöhnlichem Layout erstaunlich robust

---

### 🧠 Google Gemini – Das Analyse-Gehirn

Über die Google Gemini API (PaLM 2.5) angebunden für:

- **Section-Erkennung** (z. B. Erfahrung, Bildung, Skills)  
- **ATS-Check & Keyword-Analyse**  
- **Kritisches Feedback & Verbesserungsvorschläge**  
- **Scoring (0–100 Punkte)**

⚠️ **Datenschutz-Hinweis:**  
Nur Textauszüge werden übertragen – keine persönlichen Daten, keine Speicherungen.

---

### 📄 Google Docs – Der finale Report

- Automatische Erstellung eines Analyse-Dokuments  
- Strukturierter Report mit  
  - Executive Summary  
  - detailliertem Abschnitts-Feedback  
  - Skill Gap Analyse  
  - Verbesserungsvorschlägen  

→ Alles schön formatiert im eigenen Google Drive

---

## ⚙️ Beispiel-Workflow in n8n

1. Nutzer lädt Lebenslauf über das Formular hoch  
2. PDF wird automatisch in Text umgewandelt  
3. Gemini analysiert Inhalt nach festen Regeln  
4. Neues Google Doc wird erstellt  
5. Report wird eingefügt und formatiert  
6. Der Link zum Dokument kann übermittelt werden

---

## 🔐 Datenschutz und Sicherheit

- **100 % Self-hosted** Infrastruktur  
- **Keine Speicherung sensibler Inhalte**  
- **Kein Einsatz externer UIs oder SaaS-Dienste**  
- **Google Docs via OAuth kontrolliert & limitiert**

---

## ✅ Vorteile des Systems

| Vorteil                      | Beschreibung                                      |
|-----------------------------|---------------------------------------------------|
| Vollautomatisiert           | Lebenslauf rein → Report raus                    |
| KI-gestützt & objektiv      | Erkennt Schwächen & Potenziale                   |
| Professionelle Ausgabe      | Formatierter Report direkt in Google Docs        |
| Datenschutzkonform          | Keine fremde Cloud involviert                    |
| Einfache Nutzung            | Upload über simples Webformular                  |
| Modular & erweiterbar       | Weitere Formate, Sprachen & Analysen möglich     |

---

## 🌱 Geplante Erweiterungen

- 🧪 **Analyse mehrerer CV-Versionen im Vergleich**  
- 🎯 **Anpassung an Ziel-Stellenanzeigen (Skill-Matching)**  
- 🧠 **KI-Rewriting von Bulletpoints (inkl. Action-Verben)**  
- 🗣️ **Mehrsprachige Ausgabe (Deutsch ↔ Englisch ↔ Persisch)**

---

## 📦 Fazit

Mit einem durchdachten Setup, Open-Source-Tools und Google Gemini lässt sich ein Tool bauen, das echten Mehrwert liefert:  
**Bessere Bewerbungen, klare Reports – und das alles automatisiert und ohne externe Plattformen.**

Der nächste Karriereschritt fängt hier vielleicht mit einem besseren CV an.

---

> 📨 **Du willst auch so ein System bauen oder testen?**  
Meld dich – ich teile gerne meine Erfahrungen oder helfe beim Setup deines eigenen CV-Bots.
