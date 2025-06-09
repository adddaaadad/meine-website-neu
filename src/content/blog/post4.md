---
title: "Telegram-Bots, ChatGPT und Sicherheit: Ein Erfahrungsbericht aus der Praxis"
description: "Meine Erfahrung mit einem selbstgebauten Telegram-Bot, der ChatGPT nutzt – von Technik bis Sicherheit."
pubDate: "Jun 10 2025"
heroImage: "/post_imgh.webp"
---

## Einleitung:
In dieser Blog-Ausgabe dokumentiere ich meine eigene Erfahrung mit dem Aufbau eines Telegram-Bots, der über die OpenAI-API mit ChatGPT verbunden ist. Ziel war es, eine Anwendung zu schaffen, bei der Nutzer direkt über Telegram Fragen stellen und KI-generierte Antworten erhalten können. Was einfach klingt, stellte sich als ein komplexes Zusammenspiel aus API-Limits, Authentifizierung, Server-Infrastruktur und Sicherheitsfragen heraus.

---

## 1. Ziel des Projekts:
Ich wollte einen Telegram-Bot erstellen, der mit ChatGPT (über OpenAI) verknüpft ist. Die Idee: Ein Benutzer schreibt eine Nachricht an den Bot, diese wird an OpenAI weitergeleitet, die Antwort kommt zurück und wird automatisch gesendet.

---

## 2. Grundlegende Architektur:

- **Telegram Bot API:** Ermöglicht Nachrichtenempfang und -versand über Telegram.
- **OpenAI API:** Liefert die GPT-Antworten auf Texteingaben.
- **Python + Bibliotheken:** `python-telegram-bot`, `openai`, JSON zur Userverwaltung
- **Authentifizierungssystem:** Mit einem geheimen Einladungscode zur Begrenzung des Zugriffs auf ausgewählte Nutzer

---

## 3. Technische Herausforderungen:

### 🧩 API-Kompatibilität:
- Die `openai.ChatCompletion.create()` Methode wurde in Version 1.0 entfernt, wodurch der Bot-Ansatz mit neuer OpenAI-Version fehlschlug.
- Lösung: Migration auf neue API oder Downgrade der OpenAI-Bibliothek (`pip install openai==0.28`)

### 💳 Zahlungsprobleme:
- Die Nutzung der OpenAI-API erfordert eine Kreditkarte und ein bezahltes Konto
- Ohne gültige Zahlungsdaten zeigt die API `insufficient_quota`
- Kein Paypal möglich – nur Kreditkarte aktuell zulässig

### 💻 Infrastrukturabhängigkeit:
- Wenn der Python-Bot lokal läuft (z. B. auf Laptop) und Gerät ausgeschaltet wird, funktioniert der Bot nicht mehr
- Idee: Nutzung eines Servers oder einer NAS, wurde aber aufgrund inkompatibler Umgebung (z. B. MyCloud OS5) gestoppt

---

## 4. Sicherheitsüberlegungen:

- Es wurde ein Einladungssystem eingebaut: Nur Nutzer mit einem geheimen Code (`رمز: mayrtech2025`) erhalten Zugriff
- Zugelassene Benutzer werden in einer `users.json` Datei gespeichert
- Gespräche mit dem Bot erfolgen ausschließlich, wenn der User vorher authentifiziert wurde

---

## 5. Warum mein Projekt aktuell pausiert wurde:

- Kein Zugriff auf die OpenAI API wegen fehlender Kreditkarte
- NAS-System nicht kompatibel mit Python Runtime für Dauerbetrieb
- Projekt wird reaktiviert, sobald Zahlungsdaten verfügbar sind

---

## Fazit:
Dieses Projekt war eine intensive Lernerfahrung über API-Integration, Sicherheit, Messenger-Technologie und Infrastruktur. Wer einen eigenen Telegram-Bot mit GPT-Unterstützung bauen möchte, braucht nicht nur Coding-Wissen, sondern auch:

- Zahlungsbereitschaft (für API-Zugang)
- Server oder Hosting-Lösung
- Verständnis für Sicherheitsmechanismen in Messaging-Apps

Ich hoffe, dieser Bericht hilft anderen weiter – und vielleicht wird mein Projekt bald in einer Cloud-Umgebung wiederbelebt 😎