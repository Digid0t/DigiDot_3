# DigiDot_3
Image_generator: von Quellbild zur Erstellung von hochwertigen Icons in den Formaten PNG, JPG oder WEBP – generiert automatisch mehrere Auflösungen (512x512 bis 16x16) aus einem Quellbild.

✨ Icon-Generator mit Hybrid-Rendering

![alt text](https://img.shields.io/badge/Lizenz-MIT-blue.svg)


![alt text](https://img.shields.io/badge/Technologie-Vanilla_JS-yellow.svg)


![alt text](https://img.shields.io/badge/Abhängigkeiten-Pica_&_JSZip-orange.svg)

Ein rein clientseitiges Tool, das aus einem einzigen Bild einen vollständigen Satz von App-Icons generiert. Die Besonderheit liegt in einer fortschrittlichen Hybrid-Rendering-Pipeline, die selbst bei winzigen Größen (16x16, 32x32) für maximale Schärfe und Klarheit sorgt, wo Standard-Skalierungsalgorithmen versagen.

(Hinweis: Ersetzen Sie die obige URL durch einen echten Screenshot Ihres Tools)
Inhaltsverzeichnis

    Hauptmerkmale

    Live-Demo

    Anleitung

        Lokale Nutzung

        Deployment auf GitHub Pages

    Die Technologie dahinter: Das Problem und die Lösung

        Das Problem: Qualitätsverlust bei kleinen Größen

        Die Lösung: Hybrid-Rendering-Pipeline

    Code-Struktur im Detail

        HTML (index.html)

        CSS (im <style>-Tag)

        JavaScript (im <script>-Tag)

    Abhängigkeiten

    Mögliche Verbesserungen

    Lizenz

Hauptmerkmale

    Vollständig Client-seitig: Es werden keine Bilder auf einen Server hochgeladen. Alles geschieht sicher und privat im Browser des Benutzers.

    Hochqualitative Skalierung: Nutzt die pica.js-Bibliothek für artefaktfreie, qualitativ hochwertige Skalierung.

    Intelligentes Hybrid-Rendering: Ein spezieller Algorithmus für Icons ≤ 32x32 Pixel sorgt für unübertroffene Schärfe durch Kontrastverstärkung und Farbvereinfachung.

    Format-Auswahl: Erstellt Icons im modernen WEBP-Format, verlustfreiem PNG oder kompatiblem JPG.

    Batch-Verarbeitung: Generiert alle 11 Standardgrößen parallel und bündelt sie für den einfachen Download.

    ZIP-Download: Alle Icons werden in einer einzigen, sauber benannten icons.zip-Datei heruntergeladen.

    Keine Installation nötig: Läuft direkt aus einer einzigen HTML-Datei.

Live-Demo

Sie können dieses Tool ganz einfach selbst hosten. Die einfachste Methode ist die Verwendung von GitHub Pages.

Link zur Live-Demo: https://DEIN-GITHUB-USERNAME.github.io/DEIN-REPOSITORY-NAME/
Anleitung
Lokale Nutzung

Da das Tool keine serverseitige Logik benötigt, können Sie es direkt auf Ihrem Computer ausführen:

    Laden Sie die index.html-Datei aus diesem Repository herunter.

    Öffnen Sie die Datei index.html mit einem modernen Webbrowser (z.B. Google Chrome, Mozilla Firefox).

    Folgen Sie den Anweisungen auf dem Bildschirm:

        Wählen Sie eine Bilddatei von Ihrem Computer aus.

        Wählen Sie das gewünschte Ausgabeformat (WEBP, PNG, oder JPG).

        Klicken Sie auf "Icons generieren & herunterladen".

        Die Datei icons.zip wird automatisch in Ihrem Download-Ordner gespeichert.

Deployment auf GitHub Pages

    Forken Sie dieses Repository oder erstellen Sie ein neues.

    Laden Sie die index.html-Datei in Ihr Repository hoch.

    Gehen Sie zu Settings > Pages.

    Wählen Sie unter Source den main-Branch aus und klicken Sie auf Save.

    Nach wenigen Minuten ist Ihr Icon-Generator unter der oben angegebenen URL erreichbar.

Die Technologie dahinter: Das Problem und die Lösung
Das Problem: Qualitätsverlust bei kleinen Größen

Wenn ein detailreiches Bild auf eine winzige Größe wie 16x16 Pixel verkleinert wird, versagen herkömmliche Algorithmen. Die Pixel des Originalbildes müssen auf ein winziges Raster gequetscht werden. Dies führt zu:

    Unschärfe: Farben werden zu einem "Matsch" vermischt (Anti-Aliasing).

    Detailverlust: Dünne Linien und kleine Formen verschwinden komplett.

    Mangelnder Kontrast: Das Hauptmotiv hebt sich nicht mehr klar vom Hintergrund ab.

Die Lösung: Hybrid-Rendering-Pipeline

Dieses Tool löst das Problem, indem es je nach Zielgröße unterschiedliche Rendering-Pfade verwendet.
Zielgröße	Verwendeter Pfad	Begründung
> 32x32 Pixel	Standard-Rendering	Hohe Qualität durch pica.js ist hier ausreichend und optimal.
≤ 32x32 Pixel	Hybrid-Rendering	Ein mehrstufiger Prozess zur Erhaltung der Klarheit und Schärfe.

Die Hybrid-Rendering-Pipeline funktioniert wie folgt:

    Hochqualitativer Downscale auf eine Zwischengröße: Statt direkt auf 16px zu skalieren, wird das Originalbild zuerst auf eine größere, aber handhabbare Zwischengröße (z.B. 64x64 Pixel) verkleinert. Dies bewahrt die groben Formen viel besser.

    Pixel-Verarbeitung auf der Zwischengröße: Auf diesem Zwischenbild werden zwei entscheidende Filter angewendet:

        Kontrastverstärkung: Die Pixelwerte werden mathematisch gespreizt. Helle Farben werden heller, dunkle dunkler. Dies trennt das Motiv scharf vom Hintergrund.

        Farbquantisierung (Posterisierung): Die Anzahl der Farben wird drastisch reduziert. Statt Tausender von Farbtönen (z.B. in einem Verlauf) werden nur noch wenige, klar definierte Farbstufen verwendet. Dies verhindert die Entstehung von unscharfen "Mischfarben".

    Finaler, sauberer Downscale: Erst jetzt wird das vereinfachte, kontrastreiche Zwischenbild auf seine endgültige, winzige Größe (z.B. 16x16 Pixel) skaliert. Da die Vorlage nun klar und einfach ist, bleibt die wahrgenommene Schärfe erhalten.

Code-Struktur im Detail
HTML (index.html)

Die HTML-Datei ist das Grundgerüst. Sie enthält:

    <head>: Import der beiden entscheidenden externen Bibliotheken (pica.js und jszip.min.js) über ein CDN.

    <body>: Die gesamte Benutzeroberfläche, bestehend aus Standard-HTML-Elementen wie <input type="file">, <input type="radio"> und <button>. Die Struktur ist semantisch und auf Barrierefreiheit ausgelegt.

CSS (im <style>-Tag)

Das Styling wird direkt in der HTML-Datei gehalten, um die Portabilität zu gewährleisten.

    CSS-Variablen (:root): Das gesamte Farbschema ist zentral an einer Stelle definiert und kann leicht angepasst werden.

    Flexbox-Layout: Wird genutzt, um den Hauptcontainer auf der Seite zu zentrieren.

    Dynamische Zustände: CSS-Selektoren wie :disabled und :hover sorgen für visuelles Feedback bei der Interaktion mit den Steuerelementen.

    Lade-Animation: Eine einfache @keyframes-Animation erzeugt das rotierende Ladesymbol.

JavaScript (im <script>-Tag)

Dies ist das Gehirn des Tools. Der Code ist in logische Funktionen aufgeteilt:

    Event-Listener: Überwachen die Interaktionen des Benutzers mit dem Dateiauswahlfeld und dem Generierungs-Button und lösen die entsprechenden Aktionen aus.

    Hauptorchestrierung (generateBtn.addEventListener):

        Verwendet async/await für sauberen, asynchronen Code.

        Nutzt Promise.all(), um die Generierung aller 11 Icons parallel zu starten und zu warten, bis alle fertig sind, bevor die ZIP-Datei erstellt wird.

    Bildverarbeitungs-Funktionen:

        resizeImageStandard(): Implementiert den einfachen Pfad für größere Icons unter Verwendung von pica.resize().

        resizeImageHybrid(): Implementiert die komplexe Pipeline für kleine Icons. Dies ist die Kernfunktion für die Qualitätsverbesserung.

        applyPixelFilters(): Eine Low-Level-Funktion, die direkt auf den rohen Pixeldaten (ImageData) operiert, um die Kontrast- und Posterisierungsfilter anzuwenden.

    Hilfsfunktionen:

        loadImage(): Konvertiert die ausgewählte Datei in ein nutzbares Image-Objekt.

        setLoadingState(), downloadZip(), resetUI(): Bündeln wiederkehrende UI-Manipulationen, um den Code sauber und wartbar zu halten (DRY - Don't Repeat Yourself).

Abhängigkeiten

Dieses Tool ist auf zwei exzellente Open-Source-Bibliotheken angewiesen:

    pica.js: Eine hochperformante Bibliothek für die qualitativ hochwertige clientseitige Bildskalierung. Sie verwendet Lanczos-Filter, um bessere Ergebnisse als die native Browser-Implementierung zu erzielen.

    JSZip: Eine Bibliothek zum Erstellen, Lesen und Bearbeiten von .zip-Dateien mit JavaScript.

Mögliche Verbesserungen

    Web Worker: Für sehr große Originalbilder könnte die Bildverarbeitung die Benutzeroberfläche kurzzeitig blockieren. Die Auslagerung des Prozesses in einen Web Worker würde für ein 100% flüssiges Erlebnis sorgen.

    Konfigurierbare Filter: Fortgeschrittene Benutzer könnten von der Möglichkeit profitieren, die Stärke des Kontrasts oder die Anzahl der Farben bei der Posterisierung selbst einzustellen.

    Drag & Drop: Implementierung einer Drag-and-Drop-Zone für eine noch einfachere Dateiauswahl.

    SVG-Unterstützung: Erkennen, ob eine SVG-Datei hochgeladen wurde, und diese direkt ohne Qualitätsverlust rastern.

Lizenz

Dieses Projekt steht unter der MIT-Lizenz. Details finden Sie in der LICENSE-Datei. Sie können den Code frei verwenden, modifizieren und verbreiten.
