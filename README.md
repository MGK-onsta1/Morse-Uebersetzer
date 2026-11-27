# 📡 Morse-Übersetzer

Ein Windows-Programm (C#, WinForms, .NET 8) zum **Übersetzen**, **Lernen** und **Chatten** mit Morsecode.

![Screenshot vom Chat](screenshot-chat.png)

## Funktionen

- **Übersetzer:** Text ↔ Morse, mit Ton zum Anhören
- **Leertasten-Eingabe:** selbst morsen (kurz = Punkt, lang = Strich)
- **Lern-Modus:** einzelne Zeichen und ganze Wörter in 5 Stufen, der Punktestand wird gespeichert
- **Chat:** über WLAN, im Handy-Browser (QR-Code) oder über das Internet, mit verschlüsselten Nachrichten; man kann auch direkt mit der Leertaste in den Chat morsen
- **Ton-Einstellungen:** Tempo, Tonhöhe, Lautstärke und längere Pausen zum Lernen

## Hilfe

Dieses Programm habe ich mit grosser Hilfe von **Claude** (einer KI von Anthropic) programmiert, getestet und dokumentiert.

## Download

**[⬇ Morse-Uebersetzer.zip herunterladen](https://github.com/MGK-onsta1/Morse-Uebersetzer/raw/main/Download/Morse-Uebersetzer.zip)** (66 MB, Version 1.2). Die Datei entpacken und `Morse.exe` starten. Man muss nichts installieren.
Wie es funktioniert, steht in der **[Anleitung](ANLEITUNG.md)**.

## Dokumentation

- [DOKUMENTATION.md](DOKUMENTATION.md): mein Lernjournal
- [SITZUNG.md](SITZUNG.md): Sitzungsbericht vom 20.11.2026 mit der Planung
- [CODE-ERKLAERUNG.md](CODE-ERKLAERUNG.md): was jede Datei macht

## Selbst bauen

```
dotnet build
dotnet publish -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true -o publish
```

Schrift „Press Start 2P“: SIL Open Font License (siehe `fonts/OFL.txt`).
