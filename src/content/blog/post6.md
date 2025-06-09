---
title: "🤖 Intelligente Angebotsautomatisierung mit n8n, ChatGPT-4o und Telegram"
description: "Wie ich einen smarten Bot für Digikala, Amazon & eBay gebaut habe – mit Fokus auf Datenschutz, Flexibilität und Open-Source."
pubDate: "Jun 10 2025"
heroImage: "/angebot-bot.webp"
---

## Einleitung

Im digitalen Zeitalter, in dem Schnäppchenjagd und Automatisierung Hand in Hand gehen, habe ich ein spannendes Projekt umgesetzt:  
Ein KI-gestützter Telegram-Bot, der automatisch nach Angeboten auf Plattformen wie Digikala, Amazon und eBay Kleinanzeigen sucht –  
die Ergebnisse analysiert und direkt per Chat an mich (oder andere Nutzer) sendet.  
Das Ganze basiert auf **n8n**, **ChatGPT-4o**, einer **eigenen Datenbank** und **Telegram**.

---

## 🔧 Die Idee hinter dem Projekt

Ich wollte einen flexiblen, datenschutzfreundlichen Einkaufsassistenten, der:

- vollautomatisch nach Produkten auf verschiedenen Marktplätzen sucht  
- intelligent auf Nutzeranfragen reagiert  
- über Telegram leicht zugänglich ist  
- sich jederzeit erweitern lässt  

**Datensouveränität** war dabei essenziell: möglichst viel selbst hosten, möglichst wenig Drittanbieter.

---

## 🧩 Die eingesetzten Technologien

### 🔄 n8n – Die Schaltzentrale

- Open-Source-Workflow-Automatisierungstool  
- Lokal gehostet auf eigenem Server  
- Kontrolle über API-Schlüssel, Logs, Datenflüsse  

> Vorteile gegenüber Zapier oder Make: Keine Daten wandern ungefragt in fremde Clouds.

---

### 💬 Telegram Bot – Die Benutzeroberfläche

Erstellt über BotFather – mit einfachen Befehlen wie:

- `Was gibt’s Neues bei Digikala?`  
- `Suche Amazon-Angebote für "SSD 1TB" unter 70 €`  
- `Zeig mir eBay Kleinanzeigen für "PlayStation 5" in München`

→ Diese Anfragen triggern passende Workflows in n8n.

---

### 🧠 ChatGPT-4o – Das smarte Gehirn

Über die OpenAI-API angebunden für:

- **Intent-Erkennung** der Nutzereingaben  
- **Antwortgenerierung** und Empfehlungslogik  
- **Zusammenfassungen & Erklärungstexte**

⚠️ **Datenschutz-Hinweis:**  
Nur anonymisierte Daten (z. B. Produkttitel, Preise) werden an ChatGPT gesendet.

---

### 🗂️ Datenbank – Das Gedächtnis

Genutzt wird SQLite oder PostgreSQL, je nach Umfang.  
Gespeichert werden u. a.:

- Nutzeranfragen (pseudonymisiert)  
- bereits gesendete Angebote (Duplikatvermeidung)  
- persönliche Filter & Preisgrenzen

---

## 🔌 Anbindung an Marktplätze

### 🇮🇷 Digikala API

- `GET https://api.digikala.com/v1/incredible-offers/`  
- Verarbeitung & Filterung via n8n

---

### 🇺🇸 Amazon (geplant)

- Nutzung der **Product Advertising API**  
- Amazon-Affiliate-Konto erforderlich  
- HMAC-Signaturen nötig → Anbindung über Middleware

---

### 🇩🇪 eBay Kleinanzeigen

- Keine offizielle API  
- Web-Scraping mit **Node.js + Puppeteer**  
- Eigenes kleines Backend liefert JSON für n8n

> Auch hier: Keine personenbezogenen Daten auf fremden Servern.

---

## ⚙️ Beispiel-Workflow in n8n

1. Telegram-Nutzer gibt Befehl ein  
2. n8n erkennt den Intent (z. B. „Digikala-Angebote zeigen“)  
3. API-Request an Marktplatz  
4. Aufbereitung über Split & Set Nodes  
5. Optional: ChatGPT für Antworttext  
6. Ausgabe via Telegram `Send Message`

---

## 🔐 Datenschutz und Sicherheit

- **Self-hosting** aller Komponenten  
- **Ende-zu-Ende-Verschlüsselung** via Telegram  
- **Keine dauerhafte Chatprotokollierung**  
- **Keine Drittanbieter-Clouds ohne Kontrolle**

---

## ✅ Vorteile des Systems

| Vorteil                      | Beschreibung                              |
|-----------------------------|-------------------------------------------|
| Automatisiert & effizient   | Reagiert sofort auf Nutzeranfragen        |
| Benutzerfreundlich          | Telegram als einfache Oberfläche          |
| Datenschutzkonform          | Keine unnötige Cloudbindung               |
| KI-gestützt                 | Versteht, filtert & erklärt Angebote      |
| Multiplattformfähig         | Digikala, Amazon, eBay Kleinanzeigen      |
| Modular & erweiterbar       | Neue Quellen & Filter jederzeit möglich   |

---

## 🌱 Geplante Erweiterungen

- 🔁 **Automatische Checks per Cron**  
- 📍 **Standortfilter für eBay Kleinanzeigen**  
- 💡 **Benutzer-Profile mit Preisalarmen**  
- 🗣️ **Mehrsprachige Antworten (Deutsch ↔ Persisch)**

---

## 📦 Fazit

Mit einem klaren Konzept, Open-Source-Tools und etwas KI lässt sich ein intelligenter Bot bauen, der echte Probleme löst:  
**Zeitersparnis, bessere Übersicht und mehr Komfort bei der Produktsuche.**

Und das – ganz ohne Big-Tech-Abhängigkeit.

---

> 📨 **Du willst auch so ein System bauen?**  
Schreib mir – ich teile gerne meine Erfahrungen oder helfe bei deinem Use Case weiter.
