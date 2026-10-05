# bimetrics für Cursor und Grok Bot

bimetrics verbindet Buchhaltung, Belege, Rechnungen und E-Rechnungen für
Selbstständige und Unternehmen mit deinem KI-Assistenten. Dieses Plugin-Paket
ist für Cursor und Grok Bot vorgesehen. Es enthält die Verbindung zum
bimetrics-MCP-Server. Ein Marketplace-Eintrag oder eine bestätigte Unterstützung
beider Anwendungen ist mit diesem Paket noch nicht verbunden.

## Verbinden

Du brauchst einen bimetrics-Account und eine Firma mit freigeschaltetem
MCP-Zugang. Als Teammitglied benötigst du das entsprechende MCP-Recht für die
Firma; der Inhaber vergibt es in den Team-Einstellungen.

Nach der Installation startest du die Anmeldung über die Plugin-Ansicht deiner
Anwendung. Die OAuth-Anmeldung öffnet bimetrics im Browser. Dort wählst du
ausdrücklich die Firmen und Rechte, die du freigeben möchtest. Du kannst bei
lesendem Zugriff bleiben oder zusätzlich Lesen und Schreiben erlauben. Die
angefragten Rechte sind keine automatische Freigabe. Bei mehreren verbundenen
Firmen gibst du bei deiner Anfrage an, für welche Firma gearbeitet werden soll.

Du gibst dein Passwort ausschließlich in der bimetrics-Anmeldung ein. Das
Plugin braucht keinen API-Schlüssel und kein Client-Secret. Die zusätzliche
Berechtigung `offline_access` ermöglicht die Erneuerung der Verbindung innerhalb
ihrer Gültigkeit. Deine eigenen Firmenrechte bleiben maßgeblich. Du kannst die
Verbindung in bimetrics unter Einstellungen → MCP widerrufen.

Für eine manuelle Einrichtung in Cursor enthält `mcp.json` die Serverdefinition
für `https://app.bimetrics.de/mcp`. Übernimm den Eintrag `bimetrics` in die
`mcpServers` deiner Cursor-Konfiguration; bewahre vorhandene Servereinträge.
Die Client-ID lautet `bimetrics-cursor`. Bei einer fehlgeschlagenen Anmeldung
hilft der Support bei der Prüfung, ob der Client bereits freigeschaltet ist.

## Beispiele

- „Zeige mir für meine Firma die offenen Rechnungen und die zugehörigen Beträge.“
- „Prüfe, welche Belege für den Monatsabschluss noch Aufmerksamkeit brauchen.
  Ändere dabei nichts.“
- „Erstelle für diesen Kontakt einen Rechnungsentwurf und zeige mir die Vorschau.“
- „Lade diesen von mir ausgewählten Beleg in die angegebene Firma hoch.“

Die verfügbaren Werkzeuge hängen von deiner Freigabe, deinen Firmenrechten und
dem freigeschalteten Funktionsumfang ab. Eine ältere Verbindung kann für neue
Funktionen eine erneute Freigabe benötigen.

## Änderungen, Vorschau und Upload

Mit Schreibrechten können Änderungen sofort in bimetrics wirksam werden,
beispielsweise an Kontakten, Entwürfen, Belegen und Zuordnungen. Formuliere
deinen Auftrag deshalb mit der betroffenen Firma und der gewünschten Änderung.

Vor dem Festschreiben einer Rechnung oder eines Angebots muss der Assistent dir
die aktuelle Vorschau zeigen. Erst wenn du danach das Festschreiben beauftragst,
darf er es ausführen. Bei einer Änderung am Entwurf ist eine neue Vorschau nötig.
Eine festgeschriebene Rechnung lässt sich nicht wieder als Entwurf bearbeiten;
eine Korrektur erfolgt über ein Storno in der bimetrics-App.

Ein Beleg-Upload setzt deinen Auftrag für die konkrete Datei und Firma voraus.
Die Datei wird über einen befristeten Upload-Link übertragen. Wie beim Upload
in der App können anschließend Erkennung, Zuordnung zu Zahlungen und Buchungen
automatisch erfolgen. Kann deine Anwendung die Datei nicht übertragen, nutze
den vom Werkzeug angebotenen Weg in die bimetrics-App.

## Grenzen

Das Plugin versendet keine E-Mails, reicht keine Steueranmeldungen oder
Steuererklärungen ein und löst keine Zahlungen aus. Die KI-Auswertung ersetzt
keine fachliche Prüfung oder Steuerberatung.

MCP kann die Vorbereitung eines DATEV-Exports prüfen; der Export selbst erfolgt
in der bimetrics-App. Rechnungs-PDFs und E-Rechnungs-XML werden über die App
bereitgestellt. Wenn deine Anwendung Bilder unterstützt, können Werkzeuge
Vorschaubilder anzeigen; die verlinkte Ansicht in bimetrics bleibt maßgeblich.

## Hilfe und Lizenz

- [MCP bei bimetrics](https://bimetrics.de/mcp)
- [Support](mailto:support@bimetrics.de)
- [Cursor: MCP einrichten](https://cursor.com/docs/mcp)
- [Grok Bot: Plugins verbinden](https://cursor.com/help/grok-bot/connect-plugins)

Dieses Plugin-Paket steht unter der [MIT-Lizenz](LICENSE). Die Lizenz betrifft
die Dateien dieses Pakets. Sie erteilt keine Rechte am gehosteten
bimetrics-Backend und ersetzt keine Vereinbarung für den bimetrics-Dienst.
