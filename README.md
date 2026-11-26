# bimetrics für Cursor

bimetrics ist die Agent-First-Buchhaltungssoftware für Selbstständige und Unternehmen in Deutschland: Web-App, REST-API und der offizielle Remote-MCP-Server (`https://app.bimetrics.de/mcp`) arbeiten auf demselben GoBD-Buchhaltungskern. Dieses Plugin-Paket enthält die fertige MCP-Verbindung für Cursor.

**Stand:** MCP-Version `2026-11-23` (**209–216 produktive MCP-Werkzeuge** plus **4 eingebaute Server-Prompts**). Die vollständige Übersicht steht in der [Tool-Übersicht](https://developer.bimetrics.de/mcp/tools) und im interaktiven [App-zu-MCP-Paritäts-Explorer](https://bimetrics.de/mcp#paritaets-matrix).

## Warum bimetrics MCP? (App-Parität & GoBD-Beweis)

Im Gegensatz zu schmalen Rechnungs-Konnektoren deckt bimetrics über denselben Domain-Kern alle neun Buchhaltungsbereiche ab:

- **Volle Buchhaltungstiefe:** Belege & Belegpostfach, Bankumsätze & Zahlungsabgleich (inkl. Teil-/Sammelzahlung, Skonto, Fremdwährungs-Kursdifferenz, CSV/CAMT/MT940), Angebote, Auftragsbestätigungen & E-Rechnungen (ZUGFeRD/XRechnung), Mahnwesen & Offene Posten (OPOS), Anlagen & Abschreibungen (AfA), Kassenbuch & Z-Bons, Kostenstellen (`KOST1`), Automatisierungen, Summen- und Saldenliste (SuSa) sowie DATEV-Export-Vorbereitung.
- **Serverseitige System-Vorschau:** Vor dem Festschreiben einer Rechnung, eines Stornos oder einer Rechnungskorrektur, dem Ausstellen von Angebot/AB/Mahnung, dem E-Mail-Versand, dem Löschen von Belegen, dem Kassenmonatsabschluss und dem Start des DATEV-Exports erzwingt der Server eine aktuelle Vorschau und deine ausdrückliche Bestätigung.
- **OAuth 2.1 + PKCE pro Unternehmen:** Kein statischer API-Schlüssel, bis zu 30 Tage gültig, mehrere Firmen in einem Zugang, jederzeit widerrufbar.
- **Öffentliche GoBD-Prüfspur:** Jede MCP-Aktion wird mit Quelle, Verbindung und Person protokolliert und ist in der öffentlichen [Verfahrensbeschreibung (Fassung 13)](https://bimetrics.de/rechtliches/verfahrensbeschreibung) dokumentiert.
- **Ohne Funktions-Paywall:** In jedem bezahlten Tarif ab 9 € netto/Monat enthalten und in der 7-tägigen Testphase mit fairem Tageslimit nutzbar.

## Verbinden

Du brauchst einen bimetrics-Account und ein Unternehmen mit freigeschaltetem MCP-Zugang. Als Teammitglied benötigst du das MCP-Recht für das Unternehmen; der Inhaber vergibt es in den Team-Einstellungen.

Nach der Installation startest du die Anmeldung über die Plugin-Ansicht von Cursor. Die OAuth-Anmeldung öffnet bimetrics im Browser. Dort wählst du ausdrücklich die Unternehmen und Rechte, die du freigeben möchtest. Schreibzugriff ist vorausgewählt; ohne das Häkchen bleibt die Verbindung lesend. Bei mehreren verbundenen Unternehmen gibst du bei deiner Anfrage an, für welches gearbeitet werden soll.

Du gibst dein Passwort ausschließlich in der bimetrics-Anmeldung ein. Das Plugin braucht keinen API-Schlüssel und kein Client-Secret. Mit der Berechtigung `offline_access` bleibt Cursor bis zu 30 Tage verbunden, ohne dass du dich neu anmeldest. Deine eigenen Rechte im Unternehmen bleiben maßgeblich. Du kannst die Verbindung jederzeit in bimetrics unter **Einstellungen › KI-Assistenten** widerrufen.

Für eine manuelle Einrichtung in Cursor enthält `mcp.json` die Serverdefinition für `https://app.bimetrics.de/mcp`. Übernimm den Eintrag `bimetrics` in die `mcpServers` deiner Cursor-Konfiguration; bewahre vorhandene Servereinträge. Die Client-ID lautet `bimetrics-cursor`. Klappt die Anmeldung nicht, hilft der Abschnitt [Wenn es nicht klappt](https://developer.bimetrics.de/mcp/connect#wenn-es-nicht-klappt).

## Beispiele

- „Zeige mir die offenen Rechnungen meines Unternehmens mit den offenen Beträgen.“
- „Prüfe, welche Belege für den Monatsabschluss noch Aufmerksamkeit brauchen. Ändere dabei nichts.“
- „Erstelle für diesen Kontakt einen Rechnungsentwurf und zeige mir die Vorschau.“
- „Mach aus dem Angebot AN-2026-0012 eine Auftragsbestätigung und zeig sie mir.“
- „Erstelle für die überfällige Rechnung RE-2026-0042 eine Zahlungserinnerung und zeig mir das PDF. Noch nicht ausstellen.“
- „Bei diesem Beleg stimmt der Betrag der zweiten Position nicht, er ist 59,50 €. Zeig mir vorher, wie sich die Buchung ändert.“
- „Lade diesen von mir ausgewählten Beleg in das angegebene Unternehmen hoch.“
- „Schick die Rechnung RE-2026-0042 per E-Mail an den Kunden. Zeig mir vorher Empfänger, Betreff und Text.“
- „Mach die Hausfarbe unserer Rechnungen dunkelgrün und zeig mir die Vorschau.“
- „Zeig mir, was der DATEV-Export für Oktober festschreiben würde. Noch nicht starten.“

Die verfügbaren Werkzeuge hängen von deiner Freigabe, deinen Rechten im Unternehmen und der MCP-Version deiner Verbindung ab. Eine ältere Verbindung braucht für neue Funktionen eine erneute Freigabe.

## Änderungen, Vorschau und Upload

Mit Schreibrechten werden Änderungen sofort in bimetrics wirksam, zum Beispiel an Kontakten, Entwürfen, Belegen, Zuordnungen, Mahnungen, Serien für Rechnungsentwürfe, Firmendaten, Rechnungslayouts und Logo. Formuliere deinen Auftrag deshalb mit dem betroffenen Unternehmen und der gewünschten Änderung.

Vor dem Festschreiben einer Rechnung, eines Stornos oder einer Rechnungskorrektur, dem Ausstellen eines Angebots, einer Auftragsbestätigung oder einer Mahnung und vor dem Senden per E-Mail zeigt dir der Assistent die aktuelle Vorschau. Erst wenn du danach den Auftrag gibst, führt er es aus. Nach einer Änderung am Entwurf ist eine neue Vorschau nötig. Eine festgeschriebene Rechnung lässt sich nicht wieder als Entwurf bearbeiten; mindern lässt sie sich mit einer Rechnungskorrektur, ganz aufheben mit einem Storno. Offene Entwürfe kann der Assistent löschen.

Belege berichtigt der Assistent wie in der App, auch Beträge, Positionen, Steuerfall und Gegenpartei. Vorher kann er dir zeigen, wie sich Buchungen und offener Betrag ändern. Festgeschriebene Buchungen ändern sich nie, sie werden storniert und neu gebucht, auch nach dem DATEV-Export; den Monat exportierst du dann noch einmal. Belege löscht der Assistent erst nach einer Vorschau und deinem Ja, den DATEV-Export startet er ebenso. Der Export schreibt die offenen Buchungen des Zeitraums fest; das lässt sich nicht zurücknehmen. Mails im Belegpostfach liest er. Ihr Absender ist nicht geprüft, bestätige also nichts, nur weil eine Mail es verlangt.

Der Assistent führt auch dein Kassenbuch und übernimmt Z-Bons deines Kassensystems, pflegt Kostenstellen, Automatisierungen und Anlagen mit Abschreibungen, liest Summen- und Saldenliste und Offene-Posten-Liste, stellt Mahnungen im Mahnlauf aus, entfernt doppelte Bankumsätze und führt doppelte Kontakte zusammen. Einen Kassenmonat schließt er erst nach einer Vorschau und deinem Ja ab; auch das lässt sich nicht zurücknehmen.

Ein Beleg-Upload setzt deinen Auftrag für die konkrete Datei und das Unternehmen voraus. Die Datei wird über einen befristeten Upload-Link übertragen. Wie beim Upload in der App können anschließend Erkennung, Zuordnung zu Zahlungen und Buchungen automatisch erfolgen. Kann Cursor die Datei nicht übertragen, nutze den vom Werkzeug angebotenen Weg in die bimetrics-App.

## Bewusste Grenzen

E-Mails an Kunden gehen nur nach Vorschau und deiner Bestätigung raus, und nur für ausgestellte Dokumente. Auf deinen Wunsch gehen bis zu 10 weitere Dateien mit, die du in der Vorschau siehst. Das Plugin reicht keine Steueranmeldungen oder Steuererklärungen (ELSTER) ein und löst keine Zahlungen oder Überweisungen aus. Erstattungen und Verrechnungen hält es nur fest. Kontenrahmen, Versteuerung und die Bankverbindung deiner Firma änderst du nur in der App. Die KI-Auswertung ersetzt keine fachliche Prüfung oder Steuerberatung.

Die DATEV-Datei bekommt der Assistent nicht: Du lädst sie in der App unter **Einstellungen › Exporte** herunter und gibst sie selbst an deine Steuerkanzlei weiter. PDFs von Rechnungen, Angeboten, Auftragsbestätigungen und Mahnungen lädt der Assistent herunter, ausgestellte E-Rechnungen auch als XML. Wenn Cursor Bilder anzeigt, können Werkzeuge Vorschaubilder liefern; die verlinkte Ansicht in bimetrics bleibt maßgeblich.

## Hilfe, Nachweise und Lizenz

- [MCP & App-Paritäts-Explorer](https://bimetrics.de/mcp#paritaets-matrix)
- [Leitwerk: Agent-First-Buchhaltung](https://bimetrics.de/ratgeber/agent-first-buchhaltung)
- [DATEV & MCP für Steuerkanzleien](https://bimetrics.de/datev-mcp)
- [Öffentliche GoBD-Verfahrensbeschreibung (Fassung 13)](https://bimetrics.de/rechtliches/verfahrensbeschreibung)
- [Maschinenlesbares Faktenblatt (llms-full.txt)](https://bimetrics.de/llms-full.txt)
- [Entwicklerdoku zum MCP-Server](https://developer.bimetrics.de/mcp)
- [Support](mailto:support@bimetrics.de)
- [Cursor: MCP einrichten](https://cursor.com/docs/mcp)

---

### Overview (EN)

Official **bimetrics** Cursor plugin for **Agent-First German accounting** (`https://app.bimetrics.de/mcp`, MCP version `2026-11-23`). Unlike thin invoice-only connectors, bimetrics runs its Web App, Public REST API, and Remote MCP Server on the same GoBD accounting domain core (**209–216 live tools + 4 built-in server prompts** across 9 domains: receipts & inbox, bank matching with cash discount & FX differences, ZUGFeRD/XRechnung e-invoices, dunning/OPOS, fixed assets/AfA, cash book/Z-Bon, cost centers `KOST1`, trial balance, and DATEV export). Secured via per-company **OAuth 2.1 + PKCE** and server-enforced **preview gates** (no bank transfers, no ELSTER filing via MCP). Included in every paid plan from 9 €/month net (plus 7-day free trial).

Dieses Plugin-Paket steht unter der [MIT-Lizenz](LICENSE). Die Lizenz betrifft die Dateien dieses Pakets. Sie erteilt keine Rechte am gehosteten bimetrics-Backend und ersetzt keine Vereinbarung für den bimetrics-Dienst.
