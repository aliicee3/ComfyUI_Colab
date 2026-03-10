# ComfyUI_Colab
## First Time Setup: 
1) Laufzeittyp prüfen: Gehe oben auf Laufzeit -> Laufzeittyp ändern. Stelle sicher, dass T4 GPU (oder besser) ausgewählt ist.
2) Starte die erste Zelle. Bestätige den Zugriff auf dein Google Drive. Dies installiert ComfyUI und alle nötigen Pakete direkt auf dein Drive (ca. 2-3 Min). Achtung: Stelle sicher, dass Du genug Speicher hast, das Basasmodell allein braucht 6GB. Falls auf der Drive nicht genug platz ist, entferne das Häkchen bei *USE_GOOGLE_DRIVE*. Dann wird alles bei google lokal gespeichert aber nach Neustart einer Sitzung auch wieder gelöscht. Dh die Bilder sollte man auf dem Rechner zwischenspeichern, die Modelle muss man nach einem Neustart neu installieren.
3) Starte die Modell Download-Zelle. Dies lädt das SDXL-Modell, die 360°-LoRA und den Upscaler auf dein Drive/oder in googles temporären Speicher. Hinweis: Falls du den Drive aktiviert hast, muss das nur ein einziges mal geschehen, da die Modelle im Drive gespeichert werden.
4) Starte die dritte Zelle "Run ComfyUI with cloudflared (Recommended Way)". Warte, bis ein Link erscheint, der auf .trycloudflare.com endet. Klicke darauf, um die ComfyUI-Oberfläche zu öffnen.

## Bild Erstellung in Confy UI:
1) Workflow laden: Ziehe ein fertiges 360°-KI-Bild (aus unserem Chat/Ordner) einfach in das Browserfenster. Alle Nodes stellen sich automatisch ein.
2) Checkpoints & LoRAs: Wähle im Load Checkpoint Node sd_xl_base_1.0. Wähle im Lora Loader Node 360Redmond.
3) Prompting: * Beschreibe deine Welt im positiven Prompt (z.B. spherical panorama of a futuristic mars colony, cyberpunk style, high detail). Wichtig: Der LoRA-Trigger 360view sollte immer im Prompt stehen! Es gibt auch die Möglichkeit einen negativen Prompt unten im zweiten Promptfenster zu formulieren mit Dingen die NICHt auf dem Bild erscheinen sollen. Empfohlen ist es, beides auszufüllen.
4) Generieren: Drücke rechts auf Queue Prompt. Das erste Bild (Vorschau) erscheint nach ca. 20-40 Sekunden.

## VR-Qualität & Tiefe (Upscaling)
Damit es in der Brille nicht verpixelt aussieht, nutzt der Workflow den 4x-UltraSharp Upscaler.
- Das fertige Bild wird automatisch hochgerechnet (ca. 4096px oder 8192px Breite).
- Speichere das fertige Bild aus dem Save Image Node ab und kopiere es auf deine Brille.
- Nutze Apps wie Pigasus, DeoVR oder den Standard-Player und stelle den Modus auf 360° Mono oder Equirectangular.

## Profi-Tipp für Tiefe (3D-Effekt)
Wenn du ein echtes 3D-Gefühl willst, aktiviere den Depth-Map Node. Dieser erstellt ein Schwarz-Weiß-Bild der Entfernungen. Moderne VR-Player können damit ein plastisches Bild erzeugen!
