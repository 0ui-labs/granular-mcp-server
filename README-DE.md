# Granular MCP: Viele Workflows. Ein Kontext.

[zen_web.webm](https://github.com/user-attachments/assets/851e3911-7f06-47c0-a4ab-a2601236697c)

<div align="center">
<b>🤖 <a href="https://www.anthropic.com/claude-code">Claude</a> ODER <a href="https://github.com/google-gemini/gemini-cli">Gemini CLI</a> + [Gemini / OpenAI / Grok / OpenRouter / DIAL / Ollama / Beliebiges Modell] = Ihr ultimatives KI-Entwicklungsteam</b>
</div>

<br/>

Die ultimativen Entwicklungspartner für Ihren bevorzugten Coding Agent ([Claude](https://www.anthropic.com/claude-code) ODER [Gemini CLI](https://github.com/google-gemini/gemini-cli)) – ein Model Context Protocol-Server, der Ihnen Zugriff auf mehrere KI-Modelle
für verbesserte Codeanalyse, Problemlösung und kollaborative Entwicklung bietet.

**Echte KI-Orchestrierung mit Workflows, die sich über mehrere Aufgaben hinweg fortsetzen** – Geben Sie Claude einen komplexen
_workflow_ und lassen Sie ihn automatisch zwischen den Modellen orchestrieren. Claude behält die Kontrolle, führt die eigentliche Arbeit aus,
holt jedoch für jede Teilaufgabe die besten KI-Ergebnisse ein. Mit Tools wie [„Planner“](#3-planner---interactive-step-by-step-planning) zum
Aufteilen komplexer Projekte, [„Analyze“](#8-analyze---smart-file-analysis) zum Verstehen von Codebasen,
[„codereview“](#5-codereview---professional-code-review) für Audits, [„refactor“](#9-refactor---intelligent-code-refactoring) zur
Verbesserung der Codestruktur, [„debug“](#7-debug---expert-debugging-assistant) zur Lösung komplexer Probleme und [„precommit“](#6-precommit---pre-commit-validation) für die
Validierung von Änderungen. Claude kann während der Konversation zwischen verschiedenen Tools und Modellen wechseln,
wobei der Kontext nahtlos übernommen wird.

**Beispiel-Workflow – Claude Code:**
1. `Führen Sie eine Codeüberprüfung mit gemini pro und o3 durch und erstellen Sie mit dem Planer einen detaillierten Plan, implementieren Sie die Korrekturen und führen Sie eine abschließende Precommit-Prüfung durch, indem Sie mit der vorherigen Codeüberprüfung fortfahren`
2. Dies löst einen [`codereview`](#5-codereview---professional-code-review) Workflow aus, in dem Claude den Code durchgeht und nach allen möglichen Problemen sucht.
3. Nach mehreren Durchläufen sammelt er relevanten Code und notiert dabei Probleme.
4. Er hält einen „Vertrauensgrad“ zwischen „exploring“, „low“, „medium“, „high“ und „certain“ aufrecht, um zu verfolgen, wie sicher er Probleme finden und identifizieren konnte.
5. Erstellt eine detaillierte Liste mit kritischen -> geringfügigen Problemen.
6. Teilt die relevanten Dateien, Ergebnisse usw. mit **Gemini Pro**, um eine zweite [`codereview`](#5-codereview---professional-code-review) durchzuführen.
7. Kommt mit einer Antwort zurück und wiederholt den Vorgang mit o3, wobei er die Eingabeaufforderung ergänzt, wenn neue Erkenntnisse zutage treten.
8. Wenn er fertig ist, nimmt Claude alle Rückmeldungen auf und fasst sie in einer einzigen Liste aller kritischen -> geringfügigen Probleme zusammen, einschließlich guter Muster in Ihrem Code. Die endgültige Liste enthält neue Erkenntnisse oder Überarbeitungen, falls Claude etwas Wichtiges missverstanden oder übersehen hat und eines der anderen Modelle darauf hingewiesen hat
9. Anschließend wird der [`Planner`](#3-planner---interactive-step-by-step-planning) verwendet, um die Arbeit in einfachere Schritte zu unterteilen, wenn eine größere Umgestaltung erforderlich ist
10. Claude führt dann die eigentliche Arbeit zur Behebung der hervorgehobenen Probleme durch
11. Wenn er fertig ist, kehrt Claude zu Gemini Pro zurück, um eine [`precommit`](#6-precommit---pre-commit-validation) Überprüfung durchzuführen.

Alles in einem einzigen Konversations-Thread! Gemini Pro in Schritt 11 weiß, was von O3 in Schritt 7 empfohlen wurde! Es berücksichtigt diesen Kontext
und die Überprüfung, um die abschließende Überprüfung vor dem Commit zu unterstützen.

**Stellen Sie sich das wie Claude-Code _für_ Claude-Code vor.** Dieses MCP ist keine Zauberei. Es ist einfach **Superkleber**.

> **Denken Sie daran:** Claude behält die volle Kontrolle – aber **SIE** haben das Sagen.
> Granular ist so konzipiert, dass Claude nur bei Bedarf andere Modelle hinzuzieht – und einen sinnvollen Austausch führt.
> **Sie** sind derjenige, der die leistungsstarken Eingabeaufforderungen erstellt, die Claude dazu bringen, Gemini, Flash, O3 einzubeziehen – oder solo zu arbeiten.
> Sie sind der Lotse. Der Prompter. Der Puppenspieler.
> ### Sie sind die KI – **wirklich intelligent**.

Denn diese KI-Modelle sind [offensichtlich nicht intelligent, wenn sie geschwätzig werden →](docs/ai_banter.md)

## Schnellnavigation

- **Erste Schritte
- [Schnellstart](#quickstart-5-minutes) - In 5 Minuten startklar
- [Verfügbare Tools](#available-tools) - Übersicht über alle Tools
- [AI-to-AI-Konversationen](#ai-to-ai-conversation-threading) - Mehrrundengespräche

- **Tools-Referenz**
- [`chat`](#1-chat---general-development-chat--collaborative-thinking) - Kollaboratives Denken
- [`thinkdeep`](#2-thinkdeep---extended-reasoning-partner) - Erweiterte Argumentation
- [`challenge`](#3-challenge---critical-challenge-prompt) - Verhindert Antworten wie „Sie haben vollkommen Recht!“
- [`planner`](#4-planner---interactive-step-by-step-planning) - Interaktive Schritt-für-Schritt-Planung
- [`consensus`](#5-consensus---multi-model-perspective-gathering) - Multimodale Konsensanalyse
- [`codereview`](#6-codereview---professional-code-review) - Codeüberprüfung
- [`precommit`](#7-precommit---pre-commit-validation) - Validierung vor der Übermittlung
- [`debug`](#8-debug---expert-debugging-assistant) - Hilfe beim Debugging
- [`analyze`](#9-analyze---smart-file-analysis) - Dateianalyse
- [`refactor`](#10-refactor---intelligent-code-refactoring) - Code-Refactoring mit Fokus auf Zerlegung
- [`tracer`](#11-tracer---static-code-analysis-prompt-generator) - Call-Flow-Mapping und Abhängigkeitsverfolgung
- [`testgen`](#12-testgen---umfassende-testgenerierung) - Testgenerierung mit Randfällen
- [`secaudit`](#13-secaudit---umfassende-sicherheitsüberprüfung) - Sicherheitsüberprüfung mit OWASP-Analyse
- [`docgen`](#14-docgen---umfassende-dokumentationsgenerierung) - Dokumentationsgenerierung mit Komplexitätsanalyse

- **Erweiterte Verwendung**
- [Erweiterte Funktionen](#advanced-features) - KI-zu-KI-Konversationen, große Eingabeaufforderungen, Websuche
- [Vollständige Anleitung für Fortgeschrittene](docs/advanced-usage.md) - Modellkonfiguration, Denkmodi, Workflows, Tool-Parameter

- **Einrichtung und Support**
- [WSL-Einrichtungsanleitung](docs/wsl-setup.md) - Konfiguration des Windows-Subsystems für Linux
- [Fehlerbehebungsanleitung](docs/troubleshooting.md) - Häufige Probleme und Schritte zur Fehlerbehebung
- [Lizenz](#license) - Apache 2.0

## Warum dieser Server?

Claude ist brillant, aber manchmal benötigen Sie:
- **Geführte Workflows** - Entwicklerorientierte Prozesse, die eine systematische Untersuchung gewährleisten und eine überstürzte Analyse verhindern, indem sie sicherstellen, dass Claude den Code in jeder Phase gründlich überprüft ([`debug`](#7-debug---expert-debugging-assistant), [`precommit`](#6-precommit---pre-commit-validation), [`refactor`](#9-refactor---intelligent-code-refactoring), [`analyze`](#8-analyze---smart-file-analysis), [`codereview`](#5-codereview---professional-code-review))
- **Mehrere KI-Perspektiven** – Lassen Sie Claude zwischen verschiedenen Modellen orchestrieren, um die beste Analyse zu erhalten
- **Automatische Modellauswahl** – Claude wählt das richtige Modell für jede Aufgabe aus (oder Sie können es festlegen)
- **Ein erfahrener Entwickler als Partner** zur Validierung und Erweiterung von Ideen ([`chat`](#1-chat---general-development-chat--collaborative-thinking))
- **Eine zweite Meinung** zu komplexen Architekturentscheidungen – ergänzen Sie Claudes Denkweise mit Perspektiven von Gemini Pro, O3 oder [Dutzenden anderer Modelle über benutzerdefinierte Endpunkte](docs/custom_models.md) ([`thinkdeep`](#2-thinkdeep---extended-reasoning-partner))
- **Mehrere Expertenmeinungen einholen** – Lassen Sie verschiedene KI-Modelle Ihre Ideen diskutieren (einige unterstützend, andere kritisch), um bessere Entscheidungen zu treffen ([`consensus`](#3-consensus---multi-model-perspective-gathering))
- **Professionelle Code-Reviews** mit umsetzbarem Feedback für ganze Repositorys ([`codereview`](#4-codereview---professional-code-review))
- **Pre-Commit-Validierung** mit tiefer Analyse unter Verwendung des besten Modells für die jeweilige Aufgabe ([`precommit`](#5-precommit---pre-commit-validation))
- **Experten-Debugging** – O3 für logische Probleme, Gemini für architektonische Probleme ([`debug`](#6-debug---expert-debugging-assistant))
- **Erweiterte Kontextfenster über die Grenzen von Claude hinaus** - Delegieren Sie die Analyse an Gemini (1 Million Tokens) oder O3 (200.000 Tokens) für gesamte Codebasen, große Datensätze oder umfassende Dokumentationen
- **Modellspezifische Stärken** - Erweitertes Denken mit Gemini Pro, schnelle Iteration mit Flash, starke Argumentation mit O3, lokale Privatsphäre mit Ollama
- **Lokale Modellunterstützung** - Führen Sie Modelle wie Llama 3.2 lokal über Ollama, vLLM oder LM Studio aus, um Datenschutz und Kosten zu kontrollieren
- **Dynamische Zusammenarbeit** – Modelle können während der Analyse zusätzliche Kontextinformationen und Folgeantworten von Claude anfordern
- **Intelligente Dateiverwaltung** - Automatische Erweiterung von Verzeichnissen, Verwaltung von Token-Limits basierend auf der Modellkapazität
- **Vision-Unterstützung** - Analysieren Sie Bilder, Diagramme, Screenshots und visuelle Inhalte mit visionären Modellen
- **[Umgehen der Token-Limits von MCP](docs/advanced-usage.md#working-with-large-prompts)** - Umgehen Sie automatisch das 25K-Limit von MCP
- **[Kontextwiederherstellung über Sitzungen hinweg](docs/context-revival.md)** - Setzen Sie Gespräche auch nach dem Zurücksetzen des Kontexts von Claude fort, wobei andere Modelle den vollständigen Verlauf beibehalten

## Profi-Tipp: Kontextwiederherstellung

**Dies ist eine äußerst leistungsstarke Funktion, die nicht genug hervorgehoben werden kann**:

> Der erstaunlichste Nebeneffekt dieses Systems zur Fortsetzung von Gesprächen ist, dass selbst NACH dem Zurücksetzen oder
> Komprimieren von Claudes Kontext die Fortsetzungsinformationen im Speicher von MCP gespeichert bleiben, sodass Sie ihn bitten können, die Diskussion
> mit „o3“, und Claude wird plötzlich wiederbelebt, da O3 weiß, worüber gesprochen wurde, und
> dies so weitergibt, dass Claudes Verständnis wiederhergestellt wird. All dies, ohne Kontext zu verschwenden, indem Claude aufgefordert wird,
> lange Dokumente/Code erneut zu erfassen und ihn erneut aufzufordern, mit einem anderen Modell zu kommunizieren. Granular verwaltet dies intern. Die Antwort des Modells
> belebt Claude mit einem besseren Kontext rund um die Diskussion wieder, als es eine automatische Zusammenfassung jemals könnte.

**[📖 Lesen Sie die vollständige technische Beschreibung, wie dieses revolutionäre System funktioniert](docs/context-revival.md)**

Dieser Server koordiniert mehrere KI-Modelle als Ihr Entwicklungsteam, wobei Claude automatisch das beste Modell für jede Aufgabe auswählt oder Ihnen die Möglichkeit gibt, bestimmte Modelle für unterschiedliche Stärken auszuwählen.

<div align="center">
<img src="https://github.com/user-attachments/assets/0f3c8e2d-a236-4068-a80e-46f37b0c9d35" width="600">
</div>

**Verwendete Eingabeaufforderung:**
```
Studieren Sie den Code sorgfältig, denken Sie gründlich darüber nach, was er bewirkt, und prüfen Sie dann, ob es
in Bezug auf die Leistungsoptimierung Verbesserungsmöglichkeiten gibt. Brainstormen Sie dazu mit Gemini, um Feedback zu erhalten, und bestätigen Sie dann alle Änderungen, indem Sie
zunächst einen Unit-Test mit „measure“ hinzufügen, den aktuellen Code messen, die Optimierung implementieren und
erneut messen, um sicherzustellen, dass eine Verbesserung erzielt wurde. Teilen Sie anschließend die Ergebnisse mit. Halten Sie Gemini während der Optimierungen auf dem Laufenden.
```

Die endgültige Implementierung führte zu einer Verbesserung der JSON-Parsing-Leistung für die ausgewählte Bibliothek um 26 % und reduzierte die Verarbeitungszeit durch gezielte, kollaborative Optimierungen, die auf der Analyse von Gemini und den Verfeinerungen von Claude basierten.

## Schnellstart (5 Minuten)

### Voraussetzungen

- Python 3.10+ (3.12 empfohlen)
- Git
- **Windows-Benutzer**: WSL2 ist für Claude Code CLI erforderlich

### 1. API-Schlüssel abrufen (mindestens einer erforderlich)

**Option A: OpenRouter (Zugriff auf mehrere Modelle mit einer API)**
- **OpenRouter**: Besuchen Sie [OpenRouter](https://openrouter.ai/), um über eine API auf mehrere Modelle zuzugreifen. [Einrichtungsanleitung](docs/custom_models.md)
- Kontrollieren Sie den Modellzugriff und die Ausgabebeschränkungen direkt in Ihrem OpenRouter-Dashboard
- Konfigurieren Sie Modell-Aliase in [`conf/custom_models.json`](conf/custom_models.json)

**Option B: Native APIs**
- **Gemini**: Besuchen Sie [Google AI Studio](https://makersuite.google.com/app/apikey) und generieren Sie einen API-Schlüssel. Um mit Gemini 2.5 Pro optimale Ergebnisse zu erzielen, verwenden Sie einen kostenpflichtigen API-Schlüssel, da die kostenlose Version nur eingeschränkten Zugriff auf die neuesten Modelle bietet.
- **OpenAI**: Besuchen Sie [OpenAI Platform](https://platform.openai.com/api-keys), um einen API-Schlüssel für den Zugriff auf O3-Modelle zu erhalten.
- **X.AI**: Besuchen Sie [X.AI Console](https://console.x.ai/), um einen API-Schlüssel für den Zugriff auf GROK-Modelle zu erhalten.
- **DIAL**: Besuchen Sie die [DIAL-Plattform](https://dialx.ai/), um einen API-Schlüssel für den Zugriff auf mehrere Modelle über die einheitliche API zu erhalten. DIAL ist eine Open-Source-Plattform für die KI-Orchestrierung, die herstellerunabhängigen Zugriff auf Modelle von großen Anbietern, der Open-Source-Community und selbst gehosteten Bereitstellungen bietet. [API-Dokumentation](https://dialx.ai/dial_api)

**Option C: Benutzerdefinierte API-Endpunkte (lokale Modelle wie Ollama, vLLM)**
[Bitte lesen Sie die Einrichtungsanleitung](docs/custom_models.md#option-2-custom-api-setup-ollama-vllm-etc). Mit einer benutzerdefinierten API können Sie Folgendes verwenden:
- **Ollama**: Führen Sie Modelle wie Llama 3.2 lokal für kostenlose Inferenz aus
- **vLLM**: Selbst gehosteter Inferenzserver für Inferenz mit hohem Durchsatz
- **LM Studio**: Lokales Modell-Hosting mit OpenAI-kompatibler API-Schnittstelle
- **Text Generation WebUI**: Beliebte lokale Schnittstelle zum Ausführen von Modellen
- **Jede OpenAI-kompatible API**: Benutzerdefinierte Endpunkte für Ihre eigene Infrastruktur

> **Hinweis:** Die Verwendung mehrerer Anbieteroptionen kann zu Unklarheiten darüber führen, welcher Anbieter/welches Modell verwendet werden soll, wenn es Überschneidungen gibt.
> Wenn alle APIs konfiguriert sind, haben native APIs Vorrang, wenn es zu Konflikten bei Modellnamen kommt, wie z. B. bei „gemini” und „o3”.
> Konfigurieren Sie Ihre Modell-Aliase und vergeben Sie ihnen eindeutige Namen in [„conf/custom_models.json”](conf/custom_models.json)

### 2. Wählen Sie Ihre Installationsmethode

**Option A: Schnellinstallation mit uvx**

**Voraussetzungen**: Installieren Sie zuerst [uv](https://docs.astral.sh/uv/getting-started/installation/) (erforderlich für uvx)

<details>
<summary>Claude-Desktop-Konfiguration</summary>

Fügen Sie Folgendes zu Ihrer Datei „claude_desktop_config.json“ hinzu:
```json
{
„mcpServers“: {
„zen“: {
„command“: „sh“,
‚args‘: [
„-c“,
„exec $(which uvx || echo uvx) --from git+https://github.com/BeehiveInnovations/zen-mcp-server.git zen-mcp-server“
],
„env“: {
„PATH“: „/usr/local/bin:/usr/bin:/bin:/opt/homebrew/bin:~/.local/bin“,
‚OPENAI_API_KEY‘: „your_api_key_here“
}
}
}
}
```
</details>

<details>
<summary>Claude Code CLI-Konfiguration</summary>

Erstellen Sie eine Datei `.mcp.json` im Stammverzeichnis Ihres Projekts für die [projektbezogene Konfiguration](https://docs.anthropic.com/en/docs/claude-code/mcp#project-scope):
```json
{
„mcpServers“: {
„zen“: {
„command“: „sh“,
‚args‘: [
„-c“,
„exec $(which uvx || echo uvx) --from git+https://github.com/BeehiveInnovations/zen-mcp-server.git zen-mcp-server“
],
„env“: {
„PATH“: „/usr/local/bin:/usr/bin:/bin:/opt/homebrew/bin:~/.local/bin“,
‚OPENAI_API_KEY‘: „your_api_key_here“
}
}
}
}
```
</details>

<details>
<summary>Gemini CLI-Konfiguration</summary>

Bearbeiten Sie `~/.gemini/settings.json` und fügen Sie Folgendes hinzu:
```json
{
„mcpServers“: {
„zen“: {
„command“: „sh“,
‚args‘: [
„-c“,
"exec $(which uvx || echo uvx) --from git+https://github.com/BeehiveInnovations/zen-mcp-server.git zen-mcp-server„
],
“env„: {
“PATH„: “/usr/local/bin:/usr/bin:/bin:/opt/homebrew/bin:~/.local/bin„,
‚OPENAI_API_KEY‘: “your_api_key_here"
}
}
}
}
```

**Hinweis**: Granular MCP Server verbindet sich zwar erfolgreich mit Gemini CLI, aber der Aufruf des Tools funktioniert noch nicht richtig. Aktuelle Informationen finden Sie unter [Gemini CLI-Einrichtung](docs/gemini-setup.md).
</details>

**Funktionen:**
- **Keine Einrichtung erforderlich** – uvx erledigt alles automatisch
- **Immer auf dem neuesten Stand** - Ruft bei jedem Start die neueste Version ab
- **Keine lokalen Abhängigkeiten** - Funktioniert ohne Python-Umgebung
- **Sofort verfügbar** - Sofort einsatzbereit


**Option B: Herkömmliches Klonen und Einrichten**

```bash
# An den gewünschten Speicherort klonen
git clone https://github.com/BeehiveInnovations/zen-mcp-server.git
cd zen-mcp-server

# Mit einem Befehl wird Granular in Claude installiert
./run-server.sh

# Oder für Windows-Benutzer mit PowerShell:
./run-server.ps1

# So zeigen Sie die MCP-Konfiguration für Claude an
./run-server.sh -c

# PowerShell:
./run-server.ps1 -Config

# Weitere Informationen finden Sie in der Hilfe
./run-server.sh --help

# PowerShell:
./run-server.ps1 -Help
```

**Funktionen:**
- **Automatische Einrichtung aller Komponenten** - Python-Umgebung, Abhängigkeiten, Konfiguration
- **Konfiguriert Claude-Integrationen** - Fügt Claude Code CLI hinzu und führt durch die Desktop-Einrichtung
- **Sofort einsatzbereit** - Keine manuelle Konfiguration erforderlich
- **Funktioniert auch mit Gemini CLI** - Siehe [Gemini CLI-Einrichtung](docs/gemini-setup.md) für die Konfiguration

**Nach Updates:** Führen Sie nach `git pull` immer erneut `./run-server.sh` aus, um sicherzustellen, dass alles auf dem neuesten Stand ist.

**Windows-Benutzer:** Verwenden Sie WSL? Ausführliche Anweisungen finden Sie in der [WSL-Einrichtungsanleitung](docs/wsl-setup.md).

### 3. Fügen Sie Ihre API-Schlüssel hinzu

```bash
# Bearbeiten Sie .env, um Ihre API-Schlüssel hinzuzufügen (sofern diese nicht bereits in der Umgebung festgelegt sind)
nano .env

# Die Datei enthält mindestens einen Eintrag, der festgelegt werden muss:
# GEMINI_API_KEY=Ihr-Gemini-API-Schlüssel-hier # Für Gemini-Modelle
# OPENAI_API_KEY=Ihr-OpenAI-API-Schlüssel-hier # Für O3-Modelle
# OPENROUTER_API_KEY=Ihr-OpenRouter-Schlüssel # Für OpenRouter (siehe docs/custom_models.md)
# DIAL_API_KEY=Ihr-Dial-API-Schlüssel-hier # Für die DIAL-Plattform

# Für DIAL (optionale Konfiguration):
# DIAL_API_HOST=https://core.dialx.ai # Standard-DIAL-Host (optional)
# DIAL_API_VERSION=2024-12-01-preview # API version (optional)
# DIAL_ALLOWED_MODELS=o3,gemini-2.5-pro # Auf bestimmte Modelle beschränken (optional)

# Für lokale Modelle (Ollama, vLLM usw.):
# CUSTOM_API_URL=http://localhost:11434/v1 # Ollama-Beispiel
# CUSTOM_API_KEY= # Für Ollama leer lassen
# CUSTOM_MODEL_NAME=llama3.2 # Standardmodell

# Hinweis: Mindestens ein API-Schlüssel ODER eine benutzerdefinierte URL ist erforderlich
```

**Kein Neustart erforderlich**: Der Server liest die .env-Datei jedes Mal, wenn Claude ein Tool aufruft, sodass Änderungen sofort wirksam werden.

**Weiter**: Führen Sie nun „claude” aus Ihrem Projektordner über das Terminal aus, damit eine Verbindung zum neu hinzugefügten mcp-Server hergestellt wird.
Wenn Sie bereits eine „claude”-Code-Sitzung ausgeführt haben, beenden Sie diese bitte und starten Sie eine neue Sitzung.

#### Bei Einrichtung für Claude Desktop

**Benötigen Sie die genaue Konfiguration?** Führen Sie „./run-server.sh -c” aus, um die plattformspezifischen Einrichtungsanweisungen mit den richtigen Pfaden anzuzeigen.

1. **Öffnen Sie die Claude Desktop-Konfiguration**: Einstellungen → Entwickler → Konfiguration bearbeiten
2. **Kopieren Sie die Konfiguration**, die von „./run-server.sh -c“ angezeigt wird, in Ihre „claude_desktop_config.json“
3. **Starten Sie Claude Desktop neu**, damit die Änderungen wirksam werden

### 4. Los geht's!

Fragen Sie Claude einfach ganz natürlich:
- „Denk mit Zen genauer über dieses Architekturdesign nach“ → Claude wählt das beste Modell + „thinkdeep“
- „Führe mit Granular eine Codeüberprüfung dieses Codes auf Sicherheitsprobleme durch“ → Claude wählt möglicherweise Gemini Pro + „codereview“
- „Verwende Granular und debugge, warum dieser Test fehlschlägt, der Fehler könnte in my_class.swift liegen“ → Claude wählt möglicherweise O3 + „debug“
- „Analysiere diese Dateien mit Zen, um den Datenfluss zu verstehen“ → Claude wählt das passende Modell + „analyze“
- „Verwende Flash, um Vorschläge zur Formatierung dieses Codes basierend auf den in policy.md genannten Spezifikationen zu machen“ → Verwendet speziell Gemini Flash
- „Denk gründlich darüber nach und lass o3 diesen Logikfehler debuggen, den ich in der Funktion checkOrders() gefunden habe“ → Verwendet speziell O3
- „Brainstorme Skalierungsstrategien mit Pro. Studiere den Code, wähle deine bevorzugte Strategie aus und diskutiere mit Pro, um dich für die zwei besten Ansätze zu entscheiden“ → Verwendet speziell Gemini Pro
- „Verwende local-llama, um dieses Projekt zu lokalisieren und fehlende Übersetzungen hinzuzufügen“ → Verwendet local Llama 3.2 über eine benutzerdefinierte URL
- „Verwende zunächst local-llama für eine schnelle lokale Analyse und anschließend opus für eine gründliche Sicherheitsüberprüfung“ → Verwendet beide Anbieter nacheinander

## Verfügbare Tools

Dies sind nicht nur Tools – sie ermöglichen es Claude, wie ein echter Entwickler zu denken. Anstatt mit oberflächlichen Antworten oder flüchtigen Einsichten zu antworten,
lassen diese Workflows Claude innehalten, sich in Ihren Code vertiefen und Probleme Schritt für Schritt durchdenken
.

Das ist der Unterschied zwischen einer hastigen Vermutung und einem zweiten Paar Augen, das Ihren Code wirklich versteht. Probieren Sie es aus
und spüren Sie den Unterschied.

**Schnelle Tool-Auswahlhilfe:**
- **Brauchen Sie einen Denkpartner?** → `chat` (Ideen sammeln, zweite Meinungen einholen, Ansätze validieren)
- **Brauchen Sie tiefergehende Überlegungen?** → `thinkdeep` (erweitert die Analyse, findet Randfälle)
- **Möchten Sie Antworten wie „Sie haben vollkommen Recht!“ vermeiden?** → `challenge` (hinterfragt Annahmen, regt zu einer sorgfältigen Neubewertung an)
- **Möchten Sie komplexe Projekte aufschlüsseln?** → `planner` (schrittweise Planung, Projektstruktur, Aufschlüsselung komplexer Ideen)
- **Benötigen Sie mehrere Perspektiven?** → `consensus` (einholen Sie verschiedene Expertenmeinungen zu Vorschlägen und Entscheidungen)
- **Muss der Code überprüft werden?** → `codereview` (Fehler, Sicherheit, Leistungsprobleme)
- **Validierung vor dem Commit?** → `precommit` (Validieren Sie Git-Änderungen vor dem Commit)
- **Etwas funktioniert nicht?** → `debug` (systematische Untersuchung, schrittweise Ursachenanalyse)
- **Möchten Sie den Code verstehen?** → `analyze` (Architektur, Muster, Abhängigkeiten)
- **Muss der Code umgestaltet werden?** → `refactor` (intelligente Umgestaltung mit Fokus auf Zerlegung)
- **Benötigen Sie eine Call-Flow-Analyse?** → `tracer` (generiert Eingabeaufforderungen für die Ausführungsverfolgung und Abhängigkeitszuordnung)
- **Benötigen Sie umfassende Tests?** → `testgen` (generiert Testsuiten mit Randfällen)
- **Sicherheitsbedenken?** → `secaudit` (OWASP-Analyse, Konformitätsbewertung, Schwachstellenanalyse)
- **Code muss dokumentiert werden?** → `docgen` (generiert umfassende Dokumentation mit Komplexitätsanalyse)
- **Welche Modelle sind verfügbar?** → `listmodels` (zeigt alle konfigurierten Anbieter und Modelle an)
- **Server-Informationen?** → `version` (Versions- und Konfigurationsdetails)

**Automatikmodus:** Wenn `DEFAULT_MODEL=auto`, wählt Claude automatisch das beste Modell für jede Aufgabe aus. Sie können dies mit „Use flash for quick analysis” (Flash für schnelle Analyse verwenden) oder „Use o3 to debug this” (O3 zum Debuggen verwenden) überschreiben.

**Beispiele für die Modellauswahl:**
- Überprüfung komplexer Architekturen → Claude wählt Gemini Pro
- Schnelle Formatierungsprüfung → Claude wählt Flash
- Logisches Debugging → Claude wählt O3
- Allgemeine Erklärungen → Claude wählt Flash für mehr Geschwindigkeit
- Lokale Analyse → Claude wählt Ihr Ollama-Modell

**Profi-Tipp:** Denkmodi (für Gemini-Modelle) steuern die Tiefe im Verhältnis zu den Token-Kosten. Verwenden Sie „minimal“ oder „low“ für schnelle Aufgaben und „high“ oder „max“ für komplexe Probleme. [Weitere Informationen](docs/advanced-usage.md#thinking-modes)

**Übersicht über die Tools:**
1. [`chat`](docs/tools/chat.md) – Gemeinsames Nachdenken und Entwicklungsgespräche
2. [`thinkdeep`](docs/tools/thinkdeep.md) – Erweiterte Argumentation und Problemlösung
3. [`challenge`](docs/tools/challenge.md) – Kritische Herausforderungen, verhindert „Sie haben vollkommen Recht!“
4. [`planner`](docs/tools/planner.md) – Interaktive sequenzielle Planung für komplexe Projekte
5. [`consensus`](docs/tools/consensus.md) – Multimodale Konsensanalyse mit Standpunktsteuerung
6. [`codereview`](docs/tools/codereview.md) – Professionelle Codeüberprüfung mit Schweregraden
7. [`precommit`](docs/tools/precommit.md) – Git-Änderungen vor dem Commit validieren
8. [`debug`](docs/tools/debug.md) – Systematische Untersuchung und Fehlerbehebung
9. [`analyze`](docs/tools/analyze.md) – Allgemeine Datei- und Codeanalyse
10. [`refactor`](docs/tools/refactor.md) – Code-Refactoring mit Schwerpunkt auf Dekomposition
11. [`tracer`](docs/tools/tracer.md) – Generator für statische Codeanalyse-Prompts zur Ablaufverfolgung
12. [`testgen`](docs/tools/testgen.md) – Umfassende Testgenerierung mit Abdeckung von Randfällen
13. [`secaudit`](docs/tools/secaudit.md) – Umfassende Sicherheitsüberprüfung mit OWASP Top 10-Analyse
14. [`docgen`](docs/tools/docgen.md) – Umfassende Dokumentationsgenerierung mit Komplexitätsanalyse
15. [`listmodels`](docs/tools/listmodels.md) – Anzeige aller verfügbaren KI-Modelle, sortiert nach Anbieter
16. [`version`](docs/tools/version.md) – Abfrage der Serverversion und -konfiguration

### 1. `chat` – Allgemeiner Entwicklungs-Chat und gemeinsames Brainstorming
Ihr Denkpartner für Brainstorming, Einholen von Zweitmeinungen und Validieren von Ansätzen. Perfekt für Technologievergleiche, Architekturdiskussionen und kollaborative Problemlösung.

```
Chatten Sie mit Granular über den besten Ansatz für die Benutzerauthentifizierung in meiner React-App
```

**[📖 Weiterlesen](docs/tools/chat.md)** – Detaillierte Funktionen, Beispiele und Best Practices

### 2. `thinkdeep` – Erweiterter Denkpartner
Holen Sie sich eine zweite Meinung, um Claudes eigenes erweitertes Denken zu ergänzen. Verwendet spezielle Denkmodelle, um Annahmen zu hinterfragen, Randfälle zu identifizieren und alternative Perspektiven aufzuzeigen.

```
Die Schaltfläche wird beim Klicken nicht animiert, anscheinend wird der Klick von etwas anderem abgefangen. Verwenden Sie thinkdeep mit gemini pro, nachdem Sie den entsprechenden Code gesammelt und die Dateien übergeben haben
und finden Sie heraus, was die Ursache ist
```

**[📖 Mehr lesen](docs/tools/thinkdeep.md)** - Verbesserte Analysefunktionen und kritischer Bewertungsprozess

### 3. `challenge` – Kritische Herausforderungsaufforderung
Ermutigt zu einer sorgfältigen Neubewertung von Aussagen anstelle einer automatischen Zustimmung, insbesondere wenn Sie sich irren.
Umgibt Ihre Eingaben mit Anweisungen für kritisches Denken und ehrliche Analyse.

```
Ist es nicht eine schlechte Idee, diese Funktion zur Basisklasse hinzuzufügen?
```

Normalerweise würde Ihr bevorzugter Coding-Agent begeistert antworten: **„Sie haben vollkommen Recht!“** – und dann 
die _richtige_ Strategie komplett umkehren, ohne jemals zu erklären, warum Sie falsch liegen.

<details>
<summary>Beispiel: Ohne vs. Mit Zen</summary>

**Ohne Zen:**
![without_zen@2x](https://github.com/user-attachments/assets/64f3c9fb-7ca9-4876-b687-25e847edfd87)

**Mit Zen:**
![with_zen@2x](https://github.com/user-attachments/assets/9d72f444-ba53-4ab1-83e5-250062c6ee70)

</details>

**[📖 Mehr lesen](docs/tools/challenge.md)** - Hinterfragen Sie einen Ansatz oder validieren Sie Ideen mit Zuversicht

### 4. `planner` – Interaktive Schritt-für-Schritt-Planung
Teilen Sie komplexe Projekte oder Ideen durch schrittweises Denken in überschaubare, strukturierte Pläne auf.
Perfekt für das Hinzufügen neuer Funktionen zu einem bestehenden System, die Skalierung des Systemdesigns, Migrationsstrategien
und die Architekturplanung mit Verzweigungs- und Überarbeitungsfunktionen.

#### Profi-Tipp
Claude unterstützt `Unteraufgaben`, bei denen separate Hintergrundaufgaben erstellt und ausgeführt werden. Sie können Claude bitten,
den Planer von Zen mit zwei separaten Ideen auszuführen. Wenn dies erledigt ist, verwenden Sie das „Consensus”-Tool von Zen, um den gesamten
Plan weiterzuleiten und von zwei leistungsstarken KI-Modellen eine Expertenmeinung dazu zu erhalten, mit welchem Plan Sie zuerst arbeiten sollten! Das ist wie ein **AB**-Test
in einem Schritt, ohne Wartezeit!

```
Erstellen Sie zwei separate Unteraufgaben: Zeigen Sie mir in einer Aufgabe mit dem Planer-Tool, wie ich meiner Koch-App Unterstützung für natürliche Sprache
hinzufügen kann. In der anderen Unteraufgabe soll der Planer planen, wie ich Sprachmemos zu meiner Koch-App hinzufügen kann.
Sobald dies erledigt ist, starte einen Konsens, indem du beide Pläne an o3 weiterleitest und flash, um mir das endgültige Urteil zu geben. Welchen
setze ich zuerst um?
```

**[📖 Weiterlesen](docs/tools/planner.md)** – Schritt-für-Schritt-Planungsmethodik und Fortsetzung über mehrere Sitzungen hinweg

### 5. `consensus` – Sammeln von Perspektiven aus mehreren Modellen
Holen Sie sich verschiedene Expertenmeinungen aus mehreren KI-Modellen zu technischen Vorschlägen und Entscheidungen ein. Unterstützt die Steuerung von Standpunkten (für/gegen/neutral) und strukturierte Entscheidungsfindung.

```
Erzielen Sie einen Konsens mit Flash, das eine unterstützende Haltung einnimmt, und Gemini Pro, das kritisch bewertet, ob wir
für unsere API von REST zu GraphQL migrieren sollten. Ich brauche eine definitive Antwort.
```

**[📖 Mehr lesen](docs/tools/consensus.md)** – Multi-Modell-Orchestrierung und Entscheidungsanalyse

### 6. `codereview` – Professionelle Codeüberprüfung
Umfassende Codeanalyse mit priorisierten Rückmeldungen und Schweregraden. Dieses Workflow-Tool führt Claude durch systematische Untersuchungsschritte mit obligatorischen Pausen zwischen den einzelnen Schritten, um eine gründliche Codeüberprüfung, Problemidentifizierung und Qualitätsbewertung sicherzustellen, bevor eine Expertenanalyse bereitgestellt wird.

```
Führen Sie eine Codeüberprüfung mit gemini pro durch, insbesondere für auth.py, da ich den Eindruck habe, dass ein Teil des Codes die Sicherheitsprüfungen umgeht
und möglicherweise weitere potenzielle Schwachstellen vorhanden sind. Finden und teilen Sie den entsprechenden Code.
```

**Tipps**:
* Um zusätzliche API-Kosten zu vermeiden, fügen Sie „do not use another model“ hinzu, um den gesamten Codereview-Workflow lokal auszuführen.
* Wenn Sie unabhängig von Claudes Konfidenzgrad bei der Identifizierung von Problemen **immer** ein externes Modell konsultieren möchten (empfohlen für Code-Reviews), verwenden Sie „must codereview using <Modellname>“. Dadurch wird sichergestellt, dass das Modell auch dann konsultiert wird, wenn Claude sich über die identifizierten Probleme _sicher_ ist.


**[📖 Weitere Informationen](docs/tools/codereview.md)** – Professioneller Review-Workflow mit schrittweiser Analyse

### 7. „precommit“ – Validierung vor der Freigabe
Umfassende Überprüfung von gestuften/nicht gestuften Git-Änderungen in mehreren Repositorys. Dieses Workflow-Tool führt Claude durch eine systematische Untersuchung von Git-Änderungen, Repository-Status und Dateiänderungen in mehreren Schritten, bevor eine fachkundige Validierung erfolgt, um sicherzustellen, dass die Änderungen den Anforderungen entsprechen und Regressionen vermieden werden.

```
Führen Sie eine gründliche Pre-Commit-Prüfung mit o3 durch. Wir möchten nur kritische Probleme hervorheben, keine Blocker und keine Regressionen. Ich brauche
100 %ige Sicherheit, dass alle in FIX_ISSUE_ABC.md aufgeführten Randfälle abgedeckt sind.
```

#### Reales Beispiel:

* Ich habe Claude (sonnet-4) gebeten, einen Teil des Codes zu überarbeiten, um einen bekannten Fehler zu beheben, und ihm genaue Anweisungen gegeben.
* Die Korrektur sah korrekt aus – ebenso wie die Änderungen auf den ersten Blick.
* Noch wichtiger war, dass alle bestehenden Unit-Tests (über 540) ohne Probleme bestanden wurden. Keine Regressionen. Claude schien zuversichtlich und bereit, die Änderungen zu committen. Alles sah perfekt aus.

Dann habe ich Folgendes ausgeführt:

```text
Führe ein Precommit mit o3 durch, um zu bestätigen, dass unsere Änderungen korrekt sind und die Diffs gültig sind. Stelle sicher, dass dies keine Fehler oder
Regressionen verursacht und dass Codesmells beseitigt sind
```

Dadurch wurden die verfolgten und nicht verfolgten Änderungen/Diffs und der zugehörige Code zur gründlichen Überprüfung mit dem Zen-Tool „precommit” an o3 weitergeleitet.

Ausgabe:

```text
⏺ Ergebnisse der Precommit-Analyse – KRITISCHES PROBLEM FESTGESTELLT

Das O3-Modell hat eine Regression mit hoher Schwere und mehrere Probleme mit mittlerer/geringer Schwere in unserer Refaktorierung identifiziert. Hier ist die Zusammenfassung:

🚨 HOHE SCHWERE – MUSS VOR DEM COMMIT BEHOBEN WERDEN

...
```

Das gemeldete Problem war in Wirklichkeit ein _sehr subtiler Fehler_, der bei der kurzen Überprüfung übersehen wurde – und offenbar fehlte eine Unit-Test für genau diesen Fall
(von 540 vorhandenen Tests!) – was erklärt, warum keine Regressionen gemeldet wurden. Die Behebung war letztlich einfach, aber die
Tatsache, dass Claude (und damit auch ich) dies übersehen hatte, war eine deutliche Mahnung: Keine Anzahl von Augen ist jemals genug. Das
Problem wurde behoben, `precommit` wurde erneut mit o3 ausgeführt und ergab:

**EMPFEHLUNG: MIT COMMIT FORTFAHREN**

Gut! Dies ist nur ein Beispiel – sehen Sie sich [ein weiteres Beispiel hier](docs/tools/precommit.md) an.

**Tipps**:
* Um zusätzliche API-Kosten zu vermeiden, fügen Sie „do not use another model“ hinzu, um den gesamten Precommit-Workflow lokal auszuführen.
* Wenn Sie **immer** ein externes Modell konsultieren möchten (empfohlen für die Pre-Commit-Analyse), unabhängig davon, wie sicher Claude bei der Identifizierung von Problemen ist, verwenden Sie „must precommit using <Modellname>“. Dadurch wird sichergestellt, dass das Modell auch dann konsultiert wird, wenn Claude sich über die identifizierten Probleme _sicher_ ist.

**[📖 Mehr lesen](docs/tools/precommit.md)** – Validierung und Änderungsanalyse für mehrere Repositorys

### 8. `debug` – Experte für Debugging
Systematisches, untersuchungsgesteuertes Debugging, das Claude Schritt für Schritt durch die Ursachenanalyse führt. Dieser Workflow
 
erzwingt einen strukturierten Untersuchungsprozess, bei dem Claude in mehreren Schritten eine methodische Code-Prüfung, die Sammlung von Beweisen und 
die Bildung von Hypothesen durchführt, bevor er eine Expertenanalyse vom ausgewählten KI-Modell erhält. Wenn Claudes 
Sicherheit während des Untersuchungs-Workflows **100 %** erreicht, wird die Expertenanalyse über ein anderes Modell übersprungen, um 
Tokens und Kosten zu sparen, und Claude fährt direkt mit der Behebung des Problems fort. 

```
Siehe Protokolle unter /Users/me/project/diagnostics.log und den zugehörigen Code im Sync-Ordner.
Die Protokolle zeigen, dass die Synchronisierung funktioniert, aber manchmal hängen bleibt und dem Benutzer keine Fehler angezeigt werden.
 Finden Sie mit dem Debugging-Tool von zen mit Gemini Pro heraus, warum dies geschieht, was die Ursache ist
und wie Sie das Problem beheben können
```

**Tipps**:
* Um zusätzliche API-Kosten zu vermeiden, fügen Sie „do not use another model“ hinzu, um den gesamten Debugging-Workflow lokal auszuführen. Dies wird in den meisten Fällen empfohlen, da Claude in der Regel am Ende die Ursache mit hoher Sicherheit identifiziert.
* Wenn Sie unabhängig von Claudes Konfidenzgrad **immer** ein externes Modell konsultieren möchten, verwenden Sie „must debug using <Modellname>“. Dadurch wird sichergestellt, dass das Modell auch dann konsultiert wird, wenn Claude sich über das Problem _sicher_ ist.

Im Zweifelsfall können Sie jederzeit eine neue Eingabeaufforderung senden und Claude bitten, seine Ergebnisse mit einem anderen Modell zu teilen:

```text
Mit thinkdeep fortsetzen, Details mit o4-mini teilen, um die beste Lösung für dieses Problem zu finden
```

**[📖 Weitere Informationen](docs/tools/debug.md)** – Schrittweise Untersuchungsmethodik mit Durchsetzung des Workflows

### 9. `analyze` – Intelligente Dateianalyse
Allgemeines Verständnis und Erkundung von Code. Dieses Workflow-Tool führt Claude durch eine systematische Untersuchung der Codestruktur, Muster und architektonischen Entscheidungen in mehreren Schritten und sammelt umfassende Erkenntnisse, bevor es eine Expertenanalyse für die Architekturbewertung, Mustererkennung und strategische Verbesserungsempfehlungen liefert.

```
Verwenden Sie gemini, um main.py zu analysieren und zu verstehen, wie es funktioniert
```

**[📖 Weiterlesen](docs/tools/analyze.md)** – Umfassender Analyse-Workflow mit schrittweiser Untersuchung

### 10. `refactor` – Intelligente Code-Umgestaltung
Umfassende Refactoring-Analyse mit Top-Down-Zerlegungsstrategie. Dieses Workflow-Tool erzwingt eine systematische Untersuchung von Code-Mängeln, Zerlegungsmöglichkeiten und Modernisierungsoptionen in mehreren Schritten und gewährleistet so eine gründliche Analyse, bevor es fachkundige Refactoring-Empfehlungen mit präzisen Implementierungshinweisen liefert.

```
Verwenden Sie gemini pro, um my_crazy_big_class.m in kleinere Erweiterungen zu zerlegen
```

**[📖 Mehr lesen](docs/tools/refactor.md)** – Workflow-gesteuerte Refaktorierung mit progressiver Analyse

### 11. `tracer` – Promptgenerator für statische Codeanalyse
Erstellt detaillierte Analyse-Prompts für die Abbildung von Aufrufabläufen und die Verfolgung von Abhängigkeiten. Generiert strukturierte Analyseanfragen für präzise Ausführungsabläufe oder die Abbildung von Abhängigkeiten.

```
Verwenden Sie Granular Tracer, um zu analysieren, wie UserAuthManager.authenticate verwendet wird und warum
```

**[📖 Weiterlesen](docs/tools/tracer.md)** – Prompt-Generierung und Analysemodi

### 12. `testgen` – Umfassende Testgenerierung
Generiert umfassende Testsuiten mit Edge-Case-Abdeckung auf Basis des vorhandenen Codes und des Testframeworks. Dieses Workflow-Tool führt Claude durch eine systematische Untersuchung der Codefunktionalität, kritischer Pfade, Randfälle und Integrationspunkte über mehrere Schritte hinweg, bevor umfassende Tests mit realistischer Fehlermodusanalyse generiert werden.

```
Verwenden Sie Granular, um Tests für die Methode User.login() zu generieren
```

**[📖 Weiterlesen](docs/tools/testgen.md)** – Workflow-basierte Testgenerierung mit umfassender Abdeckung

### 13. `secaudit` – Umfassende Sicherheitsüberprüfung
Systematische OWASP-basierte Sicherheitsbewertung mit Konformitätsprüfung. Dieses Workflow-Tool führt Claude durch methodische Schritte zur Sicherheitsüberprüfung mit Zwangspausen zwischen den einzelnen Schritten, um eine gründliche Schwachstellenbewertung, Sicherheitsmusteranalyse und Konformitätsprüfung sicherzustellen, bevor eine Expertenanalyse bereitgestellt wird.

```
Führen Sie mit o3 einen Secaudit für diese E-Commerce-Webanwendung durch, wobei der Schwerpunkt auf der Sicherheit der Zahlungsabwicklung und der PCI-DSS-Compliance liegt.
```

**[📖 Weiterlesen](docs/tools/secaudit.md)** – OWASP Top 10-Analyse mit Unterstützung für Compliance-Frameworks

### 14. `docgen` – Umfassende Dokumentationserstellung
Erstellt eine gründliche Dokumentation mit Komplexitätsanalyse und Identifizierung von Fallstricken. Dieses Workflow-Tool führt Claude durch eine systematische Untersuchung der Codestruktur, der Funktionskomplexität und des Dokumentationsbedarfs in mehreren Schritten, bevor eine umfassende Dokumentation erstellt wird, die algorithmische Komplexität, Informationen zum Aufrufablauf und unerwartete Verhaltensweisen enthält, die Entwickler kennen sollten.

```
# Enthält Komplexitätsangaben in Big-O, dokumentiert Abhängigkeiten/Code-Abläufe, korrigiert veraltete Dokumente
Verwenden Sie docgen, um die UserManager-Klasse zu dokumentieren

# Enthält Komplexitätsangaben in Big-O, dokumentiert Abhängigkeiten/Code-Abläufe
Verwenden Sie docgen, um alle neuen Swift-Funktionen, die ich hinzugefügt habe, mit einer Komplexitätsanalyse zu versehen, ohne den bestehenden Code zu aktualisieren
```

**[📖 Weiterlesen](docs/tools/docgen.md)** – Workflow-basierte Dokumentationserstellung mit Erkennung von Fallstricken

### 15. `listmodels` – Verfügbare Modelle auflisten
Zeigt alle verfügbaren KI-Modelle nach Anbieter sortiert an, einschließlich Funktionen, Kontextfenstern und Konfigurationsstatus.

```
Verwenden Sie Granular, um verfügbare Modelle aufzulisten
```

**[📖 Weiterlesen](docs/tools/listmodels.md)** – Modellfunktionen und Konfigurationsdetails

### 16. `version` – Serverinformationen
Rufen Sie die Serverversion, Konfigurationsdetails und den Systemstatus für die Fehlerbehebung und Diagnose ab.

```
Welche Version von Granular habe ich?
```

**[📖 Weitere Informationen](docs/tools/version.md)** – Serverdiagnose und Konfigurationsüberprüfung

Ausführliche Informationen zu den Tool-Parametern und Konfigurationsoptionen finden Sie in der [Erweiterten Bedienungsanleitung](docs/advanced-usage.md).

### Prompt-Unterstützung

Granular unterstützt leistungsstarke strukturierte Prompts in Claude Code für den schnellen Zugriff auf Tools und Modelle:

#### Tool-Prompts
- `/zen:chat ask local-llama what 2 + 2 is` - Chat-Tool mit automatisch ausgewähltem Modell verwenden
- `/zen:thinkdeep use o3 and tell me why the code isn't working in sorting.swift` – Thinkdeep-Tool mit automatisch ausgewähltem Modell verwenden
- `/zen:planner break down the microservices migration project into manageable steps` – Planner-Tool mit automatisch ausgewähltem Modell verwenden
- `/zen:consensus use o3:for and flash:against and tell me if adding feature X is a good idea for the project. Übergeben Sie ihnen eine Zusammenfassung der Funktion. - Verwenden Sie das Konsens-Tool mit der Standardkonfiguration
- `/zen:codereview Überprüfen Sie das Sicherheitsmodul ABC` - Verwenden Sie das Codereview-Tool mit automatisch ausgewähltem Modell
- `/zen:debug Die Tabellenansicht scrollt nicht richtig, sehr ruckelig, ich vermute, der Code befindet sich in my_controller.m` - Verwenden Sie das Debug-Tool mit automatisch ausgewähltem Modell
- `/zen:analyze Untersuche diese Dateien und sag mir, ob ich das CoreAudio-Framework richtig verwende` - Verwende das Analyse-Tool mit automatisch ausgewähltem Modell
- `/zen:docgen Erstelle eine umfassende Dokumentation für die UserManager-Klasse mit Komplexitätsanalyse` - Verwende das Docgen-Tool mit automatisch ausgewähltem Modell

#### Fortsetzungsaufforderungen
- `/zen:chat fortfahren und Gemini Pro fragen, ob Framework B besser ist` - Vorherige Unterhaltung mit dem Chat-Tool fortsetzen

#### Fortgeschrittene Beispiele
- `/zen:thinkdeeper prüfen, ob der Algorithmus in @sort.py performant ist und ob es Alternativen gibt, die wir untersuchen könnten`
- `/zen:planner einen schrittweisen Plan für die Migration unseres Authentifizierungssystems zu OAuth2 erstellen, einschließlich Abhängigkeiten und Rollback-Strategien`
- `/zen:consensus Debattiere, ob wir für unsere API zu GraphQL migrieren sollten`
- `/zen:precommit Bestätige, dass diese Änderungen unseren Anforderungen in COOL_FEATURE.md entsprechen`
- `/zen:testgen Schreibe mir Tests für die Klasse ABC`
- `/zen:docgen Dokumentiere das Zahlungsabwicklungsmodul mit Fallstricken und Komplexitätsanalyse`
- `/zen:refactor Schlage eine Zerlegungsstrategie vor, erstelle einen Plan und speichere ihn in FIXES.md`

#### Syntaxformat
Das Format der Eingabeaufforderung lautet: `/zen:[Tool] [Ihre_Nachricht]`

- `[Tool]` – Name eines beliebigen verfügbaren Tools (Chat, Thinkdeep, Planner, Consensus, Codereview, Debug, Analyze, Docgen usw.)
- `[Ihre_Nachricht]` – Ihre Anfrage, Frage oder Anweisungen für das Tool

**Hinweis:** Alle Eingabeaufforderungen werden in Claude Code als „(MCP) [Tool]“ angezeigt, um zu kennzeichnen, dass sie vom MCP-Server bereitgestellt werden.

## Erweiterte Funktionen

### AI-zu-AI-Konversations-Threading

Dieser Server ermöglicht eine **echte AI-Zusammenarbeit** zwischen Claude und mehreren AI-Modellen, bei der diese sich über Tools und Konversationen hinweg koordinieren und auf den Erkenntnissen der anderen aufbauen können.

**[📖 Weitere Informationen](docs/ai-collaboration.md)** – Multi-Modell-Koordination, Konversations-Threading und kollaborative Workflows


## Konfiguration

Konfigurieren Sie den Granular MCP Server über Umgebungsvariablen in Ihrer `.env`-Datei. Unterstützt mehrere KI-Anbieter, Modellbeschränkungen, Konversationseinstellungen und erweiterte Optionen.

```env
# Schnellstart – Automatikmodus (empfohlen)
DEFAULT_MODEL=auto
GEMINI_API_KEY=Ihr-Gemini-Schlüssel
OPENAI_API_KEY=Ihr-OpenAI-Schlüssel
DIAL_API_KEY=Ihr-Dial-Schlüssel # Optional: Zugriff auf mehrere Modelle über DIAL
```

**Wichtige Konfigurationsoptionen:**
- **API-Schlüssel**: Native APIs (Gemini, OpenAI, X.AI), OpenRouter, DIAL oder benutzerdefinierte Endpunkte (Ollama, vLLM)
- **Modellauswahl**: Auto-Modus oder bestimmte Modellstandards
- **Nutzungsbeschränkungen**: Kontrollieren Sie, welche Modelle zur Kostenkontrolle verwendet werden können
- **Konversationseinstellungen**: Zeitlimit, Turn-Limits, Speicherkonfiguration
- **Denkmodi**: Token-Zuweisung für erweiterte Schlussfolgerungen
- **Protokollierung**: Debug-Levels und Transparenz der Vorgänge

**[📖 Weitere Informationen](docs/configuration.md)** – Vollständige Konfigurationsreferenz mit Beispielen

## Test

Informationen zum Ausführen von Tests finden Sie im [Testleitfaden](docs/testing.md).

## Mitwirken

Wir freuen uns über Ihre Beiträge! Bitte lesen Sie unsere umfassenden Anleitungen:
- [Anleitung zum Mitwirken](docs/contributions.md) – Code-Standards, PR-Prozess und Anforderungen
- [Hinzufügen eines neuen Anbieters](docs/adding_providers.md) – Schritt-für-Schritt-Anleitung zum Hinzufügen von KI-Anbietern

## Lizenz

Apache 2.0-Lizenz – Details finden Sie in der Datei LICENSE.

## Danksagungen

Entwickelt mit der Leistungsfähigkeit der **Multi-Model-KI**-Zusammenarbeit 🤝
- **A**ctual **I**ntelligence von echten Menschen
- [MCP (Model Context Protocol)](https://modelcontextprotocol.com) von Anthropic
- [Claude Code](https://claude.ai/code) – Ihr KI-Coding-Assistent und -Orchestrator
- [Gemini 2.5 Pro & 2.0 Flash](https://ai.google.dev/) – Erweiterte Denkfähigkeit und schnelle Analyse
- [OpenAI O3](https://openai.com/) – Starke Argumentationsfähigkeit und allgemeine Intelligenz

### Star History

[![Star History Chart](https://api.star-history.com/svg?repos=BeehiveInnovations/zen-mcp-server&type=Date)](https://www.star-history.com/#BeehiveInnovations/zen-mcp-server&Date)
