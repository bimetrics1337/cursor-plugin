# bimetrics für Cursor

bimetrics verbindet Buchhaltung, Belege, Rechnungen und E-Rechnungen für
Selbstständige und Unternehmen mit deinem KI-Assistenten. Dieses Plugin-Paket
enthält die Verbindung zum bimetrics-MCP-Server für Cursor.

Stand: MCP-Version 2026-10-16. Was jede Version kann, steht in der
[Tool-Übersicht](https://developer.bimetrics.de/mcp/tools).

## Verbinden

Du brauchst einen bimetrics-Account und ein Unternehmen mit freigeschaltetem
MCP-Zugang. Als Teammitglied benötigst du das MCP-Recht für das Unternehmen;
der Inhaber vergibt es in den Team-Einstellungen.

Nach der Installation startest du die Anmeldung über die Plugin-Ansicht von
Cursor. Die OAuth-Anmeldung öffnet bimetrics im Browser. Dort wählst du
ausdrücklich die Unternehmen und Rechte, die du freigeben möchtest. Schreibzugriff
ist vorausgewählt; ohne das Häkchen bleibt die Verbindung lesend. Bei mehreren
verbundenen Unternehmen gibst du bei deiner Anfrage an, für welches gearbeitet
werden soll.

Du gibst dein Passwort ausschließlich in der bimetrics-Anmeldung ein. Das
Plugin braucht keinen API-Schlüssel und kein Client-Secret. Mit der Berechtigung
`offline_access` bleibt Cursor bis zu 30 Tage verbunden, ohne dass du dich neu
anmeldest. Deine eigenen Rechte im Unternehmen bleiben maßgeblich. Du kannst die
Verbindung in bimetrics unter Einstellungen → MCP widerrufen.

Für eine manuelle Einrichtung in Cursor enthält `mcp.json` die Serverdefinition
für `https://app.bimetrics.de/mcp`. Übernimm den Eintrag `bimetrics` in die
`mcpServers` deiner Cursor-Konfiguration; bewahre vorhandene Servereinträge.
Die Client-ID lautet `bimetrics-cursor`. Klappt die Anmeldung nicht, hilft der
Abschnitt [Wenn es nicht klappt](https://developer.bimetrics.de/mcp/connect#wenn-es-nicht-klappt).

## Beispiele

- „Zeige mir die offenen Rechnungen meines Unternehmens mit den offenen Beträgen.“
- „Prüfe, welche Belege für den Monatsabschluss noch Aufmerksamkeit brauchen.
  Ändere dabei nichts.“
- „Erstelle für diesen Kontakt einen Rechnungsentwurf und zeige mir die Vorschau.“
- „Mach aus dem Angebot AN-2026-0012 eine Auftragsbestätigung und zeig sie mir.“
- „Erstelle für die überfällige Rechnung RE-2026-0042 eine Zahlungserinnerung und
  zeig mir das PDF. Noch nicht ausstellen.“
- „Bei diesem Beleg stimmt der Betrag der zweiten Position nicht, er ist 59,50 €.
  Zeig mir vorher, wie sich die Buchung ändert.“
- „Lade diesen von mir ausgewählten Beleg in das angegebene Unternehmen hoch.“

Die verfügbaren Werkzeuge hängen von deiner Freigabe, deinen Rechten im
Unternehmen und der MCP-Version deiner Verbindung ab. Eine ältere Verbindung
braucht für neue Funktionen eine erneute Freigabe.

## Änderungen, Vorschau und Upload

Mit Schreibrechten werden Änderungen sofort in bimetrics wirksam, zum Beispiel
an Kontakten, Entwürfen, Belegen, Zuordnungen, Mahnungen und Serien für
Rechnungsentwürfe. Formuliere deinen Auftrag deshalb mit dem betroffenen
Unternehmen und der gewünschten Änderung.

Vor dem Festschreiben einer Rechnung, einer Rechnungskorrektur oder dem
Ausstellen eines Angebots, einer Auftragsbestätigung oder einer Mahnung zeigt
dir der Assistent die aktuelle Vorschau. Erst wenn du danach den Auftrag gibst,
führt er es aus. Nach einer Änderung am Entwurf ist eine neue Vorschau nötig.
Eine festgeschriebene Rechnung lässt sich nicht wieder als Entwurf bearbeiten;
mindern lässt sie sich mit einer Rechnungskorrektur, ein Vollstorno erfolgt in
der bimetrics-App.

Belege berichtigt der Assistent wie in der App, auch Beträge, Positionen,
Steuerfall und Gegenpartei. Vorher kann er dir zeigen, wie sich Buchungen und
offener Betrag ändern. Belege mit festgeschriebenen Buchungen bleiben gesperrt.

Ein Beleg-Upload setzt deinen Auftrag für die konkrete Datei und das Unternehmen
voraus. Die Datei wird über einen befristeten Upload-Link übertragen. Wie beim
Upload in der App können anschließend Erkennung, Zuordnung zu Zahlungen und
Buchungen automatisch erfolgen. Kann Cursor die Datei nicht übertragen, nutze
den vom Werkzeug angebotenen Weg in die bimetrics-App.

## Grenzen

Das Plugin versendet keine E-Mails, Rechnungen oder Mahnungen, reicht keine
Steueranmeldungen oder Steuererklärungen ein und löst keine Zahlungen oder
Überweisungen aus. Erstattungen und Verrechnungen hält es nur fest. Die
KI-Auswertung ersetzt keine fachliche Prüfung oder Steuerberatung.

MCP kann die Vorbereitung eines DATEV-Exports prüfen; der Export selbst erfolgt
in der bimetrics-App. PDFs von Rechnungen, Angeboten, Auftragsbestätigungen und
Mahnungen lädt der Assistent herunter; die E-Rechnungs-XML gibt es in der App.
Wenn Cursor Bilder anzeigt, können Werkzeuge Vorschaubilder liefern; die
verlinkte Ansicht in bimetrics bleibt maßgeblich.

## Hilfe und Lizenz

- [MCP bei bimetrics](https://bimetrics.de/mcp)
- [Entwicklerdoku zum MCP-Server](https://developer.bimetrics.de/mcp)
- [Support](mailto:support@bimetrics.de)
- [Cursor: MCP einrichten](https://cursor.com/docs/mcp)

Dieses Plugin-Paket steht unter der [MIT-Lizenz](LICENSE). Die Lizenz betrifft
die Dateien dieses Pakets. Sie erteilt keine Rechte am gehosteten
bimetrics-Backend und ersetzt keine Vereinbarung für den bimetrics-Dienst.
