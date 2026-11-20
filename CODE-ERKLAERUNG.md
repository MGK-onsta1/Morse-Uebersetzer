# Code-Erklärung: Morse-Übersetzer

Hier steht kurz und einfach, was jede Datei macht.

## Wie hängt alles zusammen?

```
Form1 (Oberfläche)
 ├── MorseTable   → übersetzt Text ↔ Morse
 ├── MorseAudio   → macht den Ton
 ├── MorseKeyer   → erkennt Punkt/Strich bei der Leertaste
 └── LearnTrainer → Lern-Modus: Zeichen auswählen, Punkte zählen, speichern
```

`Form1` ist der „Chef“. Wenn ich einen Button drücke, ruft `Form1` die anderen Klassen auf.

## MorseTable.cs – der Übersetzer

- `Codes` ist ein `Dictionary`: Zu jedem Buchstaben gehört ein Code, z. B. `'A' → ".-"`.
- `Reverse` ist dasselbe umgekehrt: `".-" → 'A'`.
- **Text → Morse:** Den Text in Wörter teilen, jeden Buchstaben in der Tabelle nachschauen, die Codes mit Leerzeichen verbinden und die Wörter mit ` / `.
- **Morse → Text:** Bei `/` teilen (das sind die Wörter), dann bei Leerzeichen teilen (das sind die Buchstaben) und jeden Code in `Reverse` nachschauen.

## MorseAudio.cs – der Ton

- Ein Ton ist eine **Sinuswelle**: `Math.Sin(...)` gibt Zahlen zwischen -1 und 1. Das sind die Samples, die der Lautsprecher abspielt.
- 1 Einheit = `1200 / Tempo` Millisekunden. Ein Punkt dauert 1 Einheit, ein Strich 3.
- Abgespielt wird mit `waveOut` aus Windows (`winmm.dll`). Vorher war es `SoundPlayer`, aber dessen `Stop()` hat bis zu 1 Sekunde gebraucht. Dann hat die Leertaste nicht mehr richtig funktioniert.

## MorseKeyer.cs – die Leertaste

- `Press()` startet eine `Stopwatch`, `Release()` stoppt sie.
- Gedrückt **kürzer als 2 Einheiten** → Punkt, sonst → Strich.
- `Tick()` läuft alle 15 ms (über einen Timer) und misst die Pause:
  - Pause ≥ 3 Einheiten → Buchstabe fertig (Event `LetterCompleted`)
  - Pause ≥ 7 Einheiten → Wort fertig (Event `WordCompleted`)
- **Event** heisst: Der Keyer sagt „Buchstabe fertig!“, und `Form1` reagiert darauf.

## LearnTrainer.cs – der Lern-Modus

- `Next()` wählt ein zufälliges Zeichen. Zeichen mit Fehlern kommen in eine Art „Lostopf“, und zwar mehrmals. So werden sie öfter gezogen.
- `CheckCode()` / `CheckChar()` prüfen die Antwort und zählen richtig, falsch und die Serie.
- `Save()` / `Load()` speichern den Punktestand als JSON in `%AppData%\Morse\lernstand.json`.

## Form1.cs – die Oberfläche

- `KeyPreview = true`: Die Form bekommt die Tasten zuerst. So drückt die Leertaste keinen Button.
- `e.SuppressKeyPress = true`: Die Leertaste schreibt kein Leerzeichen in ein Textfeld.
- Wenn ich das Fenster wechsle, während die Taste gedrückt ist (`Deactivate`), wird sie automatisch „losgelassen“.

## Neu: Chat (aus dem Projekt MorseCode übernommen)

| Datei | Was sie macht |
|-------|---------------|
| `ChatNode.cs` | Verbindet zwei Programme direkt per **TCP**. Jede Nachricht wird mit **AES-GCM** verschlüsselt. Der Schlüssel wird aus dem Passwort berechnet. |
| `LanDiscovery.cs` | Ruft alle 2 Sekunden per **UDP-Broadcast** ins WLAN: „Ich bin da!“. So findet man Freunde automatisch. |
| `WebBridge.cs` | Ein kleiner **Webserver** im Programm. Das Handy öffnet die Seite und redet per **WebSocket** mit dem Programm. |
| `WebPage.cs` + `web/index.html` | Die Webseite für das Handy. Sie ist ins Programm eingebaut. |
| `TunnelManager.cs` | Startet *cloudflared*. Das macht aus dem Webserver einen öffentlichen Internet-Link. |
| `QrWindow.cs` | Zeigt den Link als QR-Code (mit dem NuGet-Paket `QRCoder`). |
| `ChatHistory.cs` | Speichert den Chatverlauf als JSON. |
| `AppSettings.cs` | Speichert Tempo, Ton, Lautstärke, Pausen und Namen. |
| `Form1.Chat.cs` | Der Chat-Tab. Er wird im Code gebaut, nicht im Designer. |

**Wie eine Nachricht reist:**
`Eingabe → TextToMorse → ChatNode.Broadcast (verschlüsselt) → Freund → entschlüsseln → MorseToText → Anzeige`

## Neu: Ton-Einstellungen und Wörter

- **Lautstärke:** Die Sinuswelle wird mit einer kleineren Zahl multipliziert, dann ist sie leiser.
- **Pausen ×:** Nur die Pausen zwischen Buchstaben und Wörtern werden länger. Die Punkte und Striche bleiben schnell. Das heisst **Farnsworth-Methode**, damit lernt man den „Klang“ der Buchstaben.
- **Wörter:** `LearnTrainer.Words` ist eine Wortliste. `WordsForLevel()` nimmt nur Wörter, deren Buchstaben man in der Stufe schon kann.

---

## Deine Aufgabe (ohne KI!)

Such dir **eine** Aufgabe aus und mach sie selbst:

1. **Farbe ändern:** Wenn die Leertaste gedrückt ist, wird das Feld gelb. Mach es grün.
   *Tipp:* `Form1.cs`, suche nach `Color.Gold`.
2. **Eigene Stufe:** Mach im Lern-Modus eine neue Stufe nur mit Ziffern 0–9.
   *Tipp:* `LearnTrainer.cs`, schau dir an, wie `Levels` aufgebaut ist.
3. **Start-Tempo ändern:** Das Programm soll mit Tempo 8 statt 12 starten.
   *Tipp:* `Form1.Designer.cs`, suche nach `numWpm.Value`.
4. **Schneller weiter:** Nach einer richtigen Antwort soll das nächste Zeichen schon nach 0,8 Sekunden kommen.
   *Tipp:* `Form1.cs`, suche nach `timerLearnNext.Interval`.

Danach mit **F5** starten und schauen, ob es funktioniert.
