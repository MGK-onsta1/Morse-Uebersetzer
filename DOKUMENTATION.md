# Lern-Periode-2

# 06.11.2026 | Projekt: Morse-Übersetzer

## Heute

Ich habe den Morse-Übersetzer fertig gemacht. Er übersetzt Text in Morsecode und zurück und kann den Code als Ton abspielen. Mit der Leertaste kann ich selbst morsen: kurz ist ein Punkt, lang ein Strich. Im Lern-Modus übe ich die Buchstaben. Dabei hatte ich grosse Hilfe von KI.

Ich hatte einige Fehler: Die Codetabelle stand in der falschen Datei, und die Umlaute waren kaputt.

Gelernt habe ich:
- Ein Strich ist 3-mal so lang wie ein Punkt.
- Mit einer `Stopwatch` messe ich, wie lange die Leertaste gedrückt ist.

**Status:** fertig – den Ton und die Leertaste muss ich noch testen.

**Wichtig:** Weil es viele Dateien sind, habe ich sie auf Branches hochgeladen.

![Screenshot vom Morse-Übersetzer](screenshot.png)

## Nächstes Mal

- [x] Den Ton und die Leertaste testen
- [x] Mit Hilfe der KI den Code besser verstehen
- [x] Den Punktestand im Lern-Modus speichern
- [ ] Einen kleinen Teil des Codes selbst ohne KI ändern

Danach will ich im Lern-Modus ganze Wörter üben.

# 06.11.2026 (Nachmittag) | Projekt: Morse-Übersetzer

## Heute

Ich habe die Ziele von heute Morgen bearbeitet. Ich habe den Ton und die Leertaste getestet, und der Lern-Modus speichert jetzt meinen Punktestand. Auch die neue Erklärung zum Code habe ich gelesen. Dabei hatte ich wieder grosse Hilfe von KI.

Ich hatte einen grossen Fehler: Die Leertaste hat nicht funktioniert. Das Feld blieb gelb, und es kam kein Buchstabe. Der Grund war, dass das Stoppen des Tons fast 1 Sekunde gedauert hat und das Programm so lange eingefroren war.

Gelernt habe ich:
- `SoundPlayer.Stop()` ist zu langsam. Mit `waveOut` von Windows stoppt der Ton sofort.
- Mit JSON kann ich den Punktestand in einer Datei speichern und beim Start wieder laden.

**Status:** fertig – die Leertaste erkennt jetzt „SOS SOS“ richtig.

![Screenshot von der Leertasten-Eingabe](screenshot-leertaste.png)

## Nächstes Mal

- [ ] Einen kleinen Teil des Codes selbst ohne KI ändern
- [ ] Mit Hilfe der KI die Datei `MorseAudio.cs` besser verstehen
- [ ] Den Ton selbst anhören und die beste Tonhöhe finden
- [ ] Im Lern-Modus alle 5 Stufen ausprobieren

Danach will ich im Lern-Modus ganze Wörter üben.

# 20.11.2026 | Projekt: Morsecode-Programm (Chat)

## Heute

Ich habe heute mit Claude meine Morsecode-Projektdateien direkt am Laptop durchgeschaut, um zu sehen, wie weit der Chat-Teil schon ist. Dabei habe ich gesehen, dass ich den WLAN-Chat, den Internet-Chat und sogar einen Browser-Chat mit QR-Code schon fertig eingebaut habe, inklusive Verschlüsselung der Nachrichten.

**Status:** Chat-Funktion (WLAN, Internet, Browser/QR) ist fertig und ins Programm eingebaut.

## Zusammenfassung

Übersetzer, Lern-Modus mit Fortschritt, Morsetaste mit Ton und Design sind fertig. Der Chat ist schon viel weiter als geplant: WLAN, Internet und sogar ein Browser-Chat mit QR-Code funktionieren bereits, und die Nachrichten sind verschlüsselt.

## Ausblick

Als Nächstes will ich das Programm mit Freunden in der Praxis testen, um zu sehen, wo es noch Fehler gibt. Danach will ich die Ton-Einstellungen verbessern, eine neue Übung mit ganzen Wörtern einbauen, den Chatverlauf speichern können und am Schluss eine fertige .exe mit Anleitung machen.

## Nächstes Mal

- [ ] Praxistest mit Freunden machen
- [x] Ton-Einstellungen verbessern
- [x] Übung mit ganzen Wörtern einbauen
- [x] Chatverlauf speichern
- [x] Fertige .exe + Anleitung erstellen

# 20.11.2026 (Nachmittag) | Projekt: Morse-Übersetzer

## Heute

Der Chat war nur im alten Projekt `MorseCode`. Ich habe ihn jetzt in den Morse-Übersetzer übernommen, er ist ein neuer Tab „Chat“. Ausserdem habe ich die Ton-Einstellungen verbessert (Lautstärke und längere Pausen), eine Übung mit ganzen Wörtern eingebaut und den Chatverlauf speicherbar gemacht. Am Schluss habe ich eine fertige `Morse.exe` mit Anleitung erstellt. Dabei hatte ich wieder grosse Hilfe von KI.

Ich hatte einen Fehler: Im Chat-Tab war ein Button über einer Checkbox, und links gab es einen unnötigen Scrollbalken. Ich habe die Texte kürzer gemacht.

Gelernt habe ich:
- Mit `dotnet publish` und `--self-contained` wird eine `.exe` gemacht, die auch ohne installiertes .NET läuft.
- Wenn man nur die Pausen länger macht (Farnsworth-Methode), hört man die Buchstaben beim Lernen besser.

**Status:** fertig – 24 automatische Tests sind ok. Mit echten Freunden habe ich den Chat noch nicht getestet.

![Screenshot vom Chat](screenshot-chat.png)

## Nächstes Mal

- [ ] Praxistest mit Freunden machen
- [ ] Die `Morse.exe` auf GitHub unter „Releases“ hochladen
- [ ] Mit Hilfe der KI `ChatNode.cs` besser verstehen
- [ ] Einen kleinen Teil des Codes selbst ohne KI ändern

Danach will ich mit Freunden einen ganzen Morse-Chat machen.

# 26.11.2026 | Projekt: Morse-Übersetzer

## Heute

Heute habe ich den Chat getestet. Weil meine Freunde nicht da waren, habe ich mit der KI einen „Test-Freund“ gebaut, der sich über WLAN verbindet. Dazu habe ich den Browser-Chat und den Internet-Link im Browser ausprobiert. Alles hat funktioniert: Die Nachrichten kamen überall an. Neu kann man im Chat auch **direkt mit der Leertaste morsen**: Haken setzen, morsen, mit der Rücktaste löschen und mit Enter senden. Am Schluss habe ich die Version 1.1 als neue `Morse.exe` gemacht. Dabei hatte ich wieder grosse Hilfe von KI.

Ich hatte einige Fehler: Wenn jemand ein falsches Passwort hatte, hat man das bei mir nicht gesehen. Im Browser stand oben nicht, wer neu dazugekommen ist. Wenn das Programm zweimal offen war, kam eine unverständliche englische Fehlermeldung. Im kleinen Fenster hat eine Checkbox den Knopf „Als Text…“ verdeckt. Alle vier Fehler sind jetzt behoben.

Gelernt habe ich:
- Bei TCP kann eine Verbindung „sauber“ zugehen, ohne Fehler. Darum muss man auch nach der `while`-Schleife prüfen, ob der Freund schon `hello` gesagt hat.
- Mit `catch (SocketException ex) when (...)` kann man nur einen bestimmten Fehler abfangen, z. B. `AddressAlreadyInUse`.
- `-p:EnableCompressionInSingleFile=true` macht die `.exe` nur halb so gross (72 MB statt 154 MB).

**Status:** fertig – WLAN, Browser, Internet-Link und Morsetaste im Chat funktionieren. Mit echten Freunden und einem echten Handy habe ich es aber noch nicht getestet.

Der Morse-Übersetzer kann übersetzen, Morse beibringen und jetzt auch einen Chat nur mit der Leertaste.

![Screenshot: Morsetaste im Chat](screenshot-morsetaste.jpg)

## Nächstes Mal

- [ ] Praxistest mit echten Freunden und Handy machen
- [ ] Die Erklärung von `ChatNode.cs` in [CODE-ERKLAERUNG.md](CODE-ERKLAERUNG.md) lesen und die 3 Testfragen beantworten
- [ ] Aufgabe 5 oder 6 aus der Code-Erklärung selbst ohne KI machen

Danach will ich mit Freunden einen ganzen Morse-Chat nur mit der Leertaste machen.
