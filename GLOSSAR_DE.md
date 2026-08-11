# Glossar: AI Engineering

## A

### A2A (Agent2Agent)

Ein Protokoll für die Verständigung zwischen eigenständigen Agenten, auch über Organisationsgrenzen hinweg. Agenten geben bekannt, was sie können, und beauftragen einander.

**Einordnung:** Ergänzt MCP, statt es zu ersetzen. Grobe Aufteilung: MCP verbindet einen Agenten mit Werkzeugen, A2A verbindet Agenten miteinander. Sicherheitsseitig der schwierigste der drei Fälle, weil Vertrauen und Rechte über eine fremde Organisation hinweg begründet werden müssen.

**Mehr:** [ACP vs MCP vs A2A, Vergleich](https://www.morphllm.com/comparisons/acp-vs-mcp-vs-a2a)

### ACP (Agent Client Protocol)

Ein Protokoll für die Verbindung zwischen einem Agenten und seiner Arbeitsumgebung, in der Regel einem Editor oder einer IDE. Es regelt, wie der Agent Dateien sieht, Änderungen vorschlägt und Rückmeldung erhält.

**Einordnung:** Das Kürzel ist doppelt belegt. Es steht sowohl für Agent Client Protocol als auch für Agent Communication Protocol, ein REST-basiertes Verfahren zur Koordination mehrerer Agenten innerhalb einer Organisation. Vor der Diskussion klären, welches gemeint ist. Beide sind deutlich weniger verbreitet als MCP.

**Mehr:** [ACP vs MCP vs A2A, Vergleich](https://www.morphllm.com/comparisons/acp-vs-mcp-vs-a2a)

### Agent

Ein Sprachmodell in einer Schleife mit Werkzeugen. Es bekommt eine Aufgabe, entscheidet über den nächsten Schritt, ruft ein Werkzeug auf, betrachtet das Ergebnis und wiederholt das, bis die Aufgabe erledigt ist oder eine Grenze greift.

**Einordnung:** Der am stärksten überdehnte Begriff im Feld. Vieles, was als Agent verkauft wird, ist eine feste Abfolge von Modellaufrufen ohne eigene Entscheidung über den nächsten Schritt. Die brauchbare Prüffrage lautet: Entscheidet das System selbst, wann es aufhört?

**Mehr:** [Building effective agents, Anthropic](https://www.anthropic.com/engineering/building-effective-agents)

### Agentic Workflow

Ein Ablauf, in dem ein Modell über mehrere Schritte hinweg selbst über den nächsten Schritt entscheidet, im Unterschied zu einer fest verdrahteten Kette von Aufrufen.

**Einordnung:** Sammelbegriff mit weichen Rändern. Agent bezeichnet die Komponente, Agentic Workflow den Ablauf. Die Trennlinie zum Workflow verläuft an der Frage, wer über den nächsten Schritt entscheidet.

**Mehr:** [Building effective agents, Anthropic](https://www.anthropic.com/engineering/building-effective-agents)

### AGENTS.md und CLAUDE.md

Textdateien im Projektverzeichnis, die einem Coding-Agenten dauerhaft mitgeben, was er über das Projekt wissen soll: Aufbau, Befehle, Konventionen und Dinge, die er unterlassen soll. Der Inhalt wandert zu Beginn jeder Sitzung in den Kontext.

**Einordnung:** AGENTS.md ist das werkzeugübergreifende Format, inzwischen unter dem Dach der Linux Foundation und in zehntausenden Repositories verbreitet. CLAUDE.md ist das native und reichhaltigere Format von Claude Code, das AGENTS.md zusätzlich liest. Zwei praktische Punkte: Der Inhalt kostet in jeder Sitzung Kontext, weshalb kurz besser ist als vollständig. Und die Datei stammt aus dem Repository, ist also eine Eingabe wie jede andere und damit ein möglicher Träger für Prompt Injection in fremden oder geteilten Projekten.

**Mehr:** [AGENTS.md Spec und Vergleich zu CLAUDE.md](https://www.morphllm.com/agents-md-guide)

### AI Council

Ein bereichsübergreifendes Gremium, das die AI-Nutzung einer Organisation steuert: Es legt Richtlinien fest, gibt Anwendungsfälle frei oder stoppt sie und verteilt Verantwortung über IT, Recht, Sicherheit und Fachbereiche. Häufiger unter dem Namen AI Governance Committee.

**Einordnung:** Organisatorischer Begriff, kein technischer — verwandt mit Shadow AI, das genau dann entsteht, wenn ein solches Gremium fehlt oder zu langsam ist. Treiber sind Regulierung (EU AI Act) und Normen wie ISO/IEC 42001. Vom AI Ethics Board zu unterscheiden, das eher beratend und übergeordnet ist.

### Alignment

Die Ausrichtung eines Modells darauf, dass sein Verhalten den Absichten und Werten des Betreibers entspricht, auch in Fällen, die im Training nicht vorkamen. Umfasst Methoden wie RLHF, explizite Regeln (Constitutional AI) und nachgelagerte Guardrails.

**Einordnung:** Oberbegriff, keine einzelne Technik. Perfekte Ausrichtung ist ungelöst; in der Praxis geht es um Grade und messbare Grenzen, nicht um einen Zustand „gelöst". Nicht zu verwechseln mit Guardrail, das zur Laufzeit kontrolliert — Alignment sitzt schon im Modell.

**Mehr:** [AI alignment, Wikipedia](https://en.wikipedia.org/wiki/AI_alignment)

## C

### Chain-of-Thought (CoT)

Eine Prompting-Technik, bei der das Modell die Zwischenschritte zu einer Antwort ausschreibt, statt nur das Endergebnis zu nennen. Das verbessert mehrschrittige Aufgaben wie Rechnen und Logik spürbar.

**Einordnung:** Technik, nicht Modelltyp — abzugrenzen vom Reasoning Model, das dieses Verhalten eintrainiert und die Ableitung meist verbirgt. Die ausgeschriebene Kette ist keine verlässliche Erklärung des tatsächlichen Rechenwegs und taugt nicht als Nachweis. Kostet zusätzliche Token.

**Mehr:** [Chain-of-Thought Prompting Elicits Reasoning in LLMs, Originalarbeit 2022](https://arxiv.org/abs/2201.11903)

### Chunking

Dokumente werden in kleinere Stücke zerlegt, damit sie einzeln indiziert, durchsucht und in den Kontext geladen werden können. Größe und Schnittkanten bestimmen, welche Zusammenhänge erhalten bleiben.

**Einordnung:** Der unauffälligste Hebel in RAG-Systemen und oft der wirksamste. Ein Schnitt mitten durch eine Tabelle oder eine Bedingung macht den Treffer wertlos, ohne dass das Retrieval-Ergebnis schlecht aussieht.

**Mehr:** [Guide to Chunking Strategies for RAG, Zilliz](https://zilliz.com/learn/guide-to-chunking-strategies-for-rag)

### Computer Use

Das Modell bedient eine grafische Oberfläche, indem es Bildschirmaufnahmen liest und Maus- und Tastatureingaben erzeugt. Gedacht für Systeme, die keine Schnittstelle anbieten.

**Einordnung:** Die breiteste Angriffsfläche unter den Werkzeugarten, weil der Bildschirminhalt selbst Anweisungen tragen kann und beliebige Fremdinhalte darauf landen. Dazu langsam, teuer und empfindlich gegenüber Layoutänderungen, was die Testautomatisierung seit Jahrzehnten kennt.

### Confused Deputy

Eine Komponente mit Berechtigungen wird von jemandem ohne diese Berechtigungen dazu gebracht, ihre Autorität in dessen Sinn einzusetzen. Der Begriff geht auf Norm Hardy zurück, 1988, und ist damit deutlich älter als Sprachmodelle.

**Einordnung:** Die präziseste Beschreibung dafür, warum Prompt Injection überhaupt gefährlich ist. Ein Agent trägt die Rechte des Nutzers und führt Anweisungen aus unvertrauenswürdigem Material aus. Das Problem sind die delegierten Rechte, nicht der Text.

**Mehr:** [Confused deputy problem, Wikipedia](https://en.wikipedia.org/wiki/Confused_deputy_problem)

### Context Engineering

Die Gestaltung dessen, was im Context Window landet. Ein Modell kann nur über Informationen urteilen, die es bekommt, weshalb bessere Auswahl oft mehr bringt als ein besseres Modell. Dazu gehören RAG, Memory, Kompression, Chunking, Ranking, die Auswahl der Gesprächshistorie und das Zurückspielen von Tool-Ergebnissen.

**Einordnung:** Der Begriff betont die Auswahl der Information, die ein Modell bekommt, nicht deren Formulierung. Das grenzt ihn von Prompt Engineering ab, das an der Formulierung des einzelnen Aufrufs ansetzt.

**Mehr:** [Effective context engineering for AI agents, Anthropic](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)

### Context Poisoning

Unvertrauenswürdiger Inhalt gelangt in das Context Window und beeinflusst alle folgenden Entscheidungen. Quellen sind abgerufene Dokumente, Tool-Ergebnisse, Webseiten, Dateien im Projekt oder ein persistenter Memory-Speicher.

**Einordnung:** Wird uneinheitlich verwendet und überschneidet sich mit Prompt Injection. Brauchbare Trennung: Prompt Injection beschreibt die eingeschleuste Anweisung, Context Poisoning den Zustand danach, in dem die falsche Information weiterwirkt. Bei persistentem Speicher überlebt sie die Sitzung, dann spricht man von Memory Poisoning.

**Mehr:** [Poison everywhere: No output from your MCP server is safe, CyberArk](https://www.cyberark.com/resources/threat-research-blog/poison-everywhere-no-output-from-your-mcp-server-is-safe)

### Context Rot

Mit wachsender Eingabelänge sinkt die Genauigkeit, lange bevor das Context Window ausgeschöpft ist. Ursachen sind die ungleiche Aufmerksamkeit über die Position, Verdünnung bei vielen Token und ähnlich klingende, aber irrelevante Inhalte.

**Einordnung:** Die Chroma-Untersuchung von 2025 zeigt den Effekt über 18 Frontier-Modelle hinweg. Praktische Folge: Die beworbene Fenstergröße ist keine nutzbare Arbeitsgröße. Wer lange Kontexte fährt, sollte die eigene Grenze messen statt sie dem Datenblatt zu entnehmen.

**Mehr:** [Context Rot, Chroma Research](https://www.trychroma.com/research/context-rot)

### Context Window

Die maximale Menge an Token, die ein Modell bei einem Aufruf gleichzeitig verarbeiten kann. Alles, was in die Antwort einfließen soll, muss hineinpassen: System Prompt, Historie, abgerufene Dokumente, Tool-Ergebnisse.

**Einordnung:** Ein großes Fenster ersetzt keine Auswahl. Die Genauigkeit sinkt bereits deutlich vor der Obergrenze, siehe Context Rot. Ein Teileffekt davon ist Lost in the Middle: Modelle beachten Anfang und Ende der Eingabe zuverlässiger als die Mitte.

**Mehr:** [Effective context engineering for AI agents, Anthropic](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)

## D

### Data Poisoning

Manipulierte oder bösartige Daten gelangen ins Training oder Fine-Tuning eines Modells und prägen dauerhaft dessen Verhalten, etwa als Hintertür oder gezielte Falschausgabe. Anders als beim Context Poisoning, das zur Laufzeit wirkt, sitzt der Schaden hier in den Gewichten.

**Einordnung:** In der OWASP-Liste als LLM04 Data and Model Poisoning geführt. Schwer zu entdecken, weil das Modell normal wirkt, bis der Auslöser kommt. Die Gegenmaßnahme liegt in Herkunft und Prüfung der Daten und damit nah an der Model Supply Chain.

**Mehr:** [OWASP Top 10 for LLM Applications 2025, PDF](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf)

### Determinism und Reproducibility

Determinismus heißt: gleiche Eingabe, gleiche Ausgabe. Reproduzierbarkeit heißt: Ein Lauf lässt sich später nachvollziehbar wiederholen, inklusive Modellversion, Parametern und Eingaben.

**Einordnung:** Beides ist bei LLMs schwächer, als es die Testerfahrung aus klassischer Software erwarten lässt. Selbst bei Temperature 0 führen die Reihenfolge von Gleitkommaoperationen auf der GPU, Batching und das Routing in Mixture-of-Experts-Modellen zu abweichenden Ausgaben. Für Tests folgt daraus: auf Eigenschaften prüfen statt auf Zeichengleichheit, und mehrfach laufen lassen.

**Mehr:** [Reproducibility, vLLM-Dokumentation](https://docs.vllm.ai/en/v0.9.1/usage/reproducibility.html)

### Distillation

Ein großes Modell dient als Lehrer für ein kleineres, das dessen Verhalten nachbildet. Ergebnis ist ein günstigeres und schnelleres Modell mit engerem Können.

**Einordnung:** Der übliche Weg zu kleinen Modellen, die auf einer Aufgabe fast an große heranreichen. Der Verlust zeigt sich an den Rändern, also bei ungewöhnlichen Eingaben, die im Lehrmaterial fehlten.

**Mehr:** [Distilling the Knowledge in a Neural Network, Originalarbeit 2015](https://arxiv.org/abs/1503.02531)

## E

### Embedding

Ein Text wird in einen Vektor aus Zahlen übersetzt, dessen Lage im Raum inhaltliche Ähnlichkeit abbildet. Grundlage der Vector Search.

**Einordnung:** Ähnlichkeit ist weder Relevanz noch Wahrheit. Zwei gegenteilige Aussagen liegen oft dicht beieinander, weil sie vom selben Thema handeln. Praktisch wichtig: Ein Wechsel des Embedding-Modells entwertet einen bestehenden Index vollständig, der Bestand muss neu berechnet werden.

### Eval

Eine wiederholbare Messung der Systemqualität gegen einen festen Satz von Fällen mit bekanntem Erwartungswert. Ergebnis ist eine Kennzahl über die Zeit, keine einzelne Ja-Nein-Aussage.

**Einordnung:** Der Begriff deckt sehr Unterschiedliches ab, von einer Handvoll Beispiele bis zu ausgewachsenen Benchmarks. Beim Lesen fremder Eval-Ergebnisse lohnt immer die Frage, wer die Testfälle geschrieben hat.

**Mehr:** [OpenAI Evals, Framework und Beispiele](https://github.com/openai/evals)

### Eval Harness

Die Infrastruktur, die eine Eval ausführt: Testfälle laden, das Modell aufrufen, Ausgaben einsammeln, die Bewertung anwenden, Ergebnisse ablegen und über die Zeit vergleichbar halten.

**Einordnung:** Vom Agent-Harness zu unterscheiden. Das eine führt das System im Betrieb aus, das andere führt Messungen darüber aus. Gleicher Wortstamm, verschiedene Sache. Der Vorfall bei OpenAI im Juli 2026 fand in einem Eval Harness statt.

**Mehr:** [OpenAI Evals, Framework und Beispiele](https://github.com/openai/evals)

### Excessive Agency

Ein System darf mehr, als seine Aufgabe verlangt: zu viele Werkzeuge, zu weite Rechte, zu wenige Bestätigungsschritte. In der OWASP-Liste als LLM06 geführt.

**Einordnung:** Die häufigste selbstgemachte Schwachstelle, weil weite Rechte die Entwicklung bequemer machen und niemand sie später zurücknimmt. Brauchbare Prüffrage: Welche Aktion könnte dieses System auslösen, die sich nicht rückgängig machen lässt?

**Mehr:** [OWASP Top 10 for LLM Applications 2025, PDF](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf)

## F

### Fine-Tuning

Ein vortrainiertes Modell wird mit eigenen Beispielen weitertrainiert, um Format, Ton oder Fachverhalten zu prägen.

**Einordnung:** Taugt für Form und Verhalten, schwach für Wissen. Wer Fakten aktuell halten will, fährt mit RAG besser, weil sich ein Dokument austauschen lässt und ein Gewicht nicht. Jedes Fine-Tuning erzeugt zudem ein eigenes Artefakt, das versioniert, getestet und gepflegt werden will.

**Mehr:** [RAG vs. Fine-tuning, IBM](https://www.ibm.com/think/topics/rag-vs-fine-tuning)

### Forward Engineering

Im ursprünglichen Sinn die Richtung von Anforderungen und Entwurf zur lauffähigen Implementierung, also das Gegenstück zum Reverse Engineering. Im AI-Umfeld erweitert auf das Bauen von AI-nativen Anwendungen aus Geschäftsanforderungen heraus, im Unterschied zur Modernisierung von Bestehendem.

**Einordnung:** Vorsicht. Der Begriff wird im AI-Umfeld gelegentlich zu einer übergreifenden Schicht über der gesamten Systementwicklung umgedeutet, was seinen ursprünglichen Sinn – das Gegenstück zum Reverse Engineering – verwischt. Dazu kommt Verwechslungsgefahr mit Forward Deployed Engineering, 2026 ein präsenter Begriff mit anderer Bedeutung: Entwickler, die beim Kunden sitzen und dort ausliefern.

**Mehr:** [What Is Forward Engineering](https://luvina.net/forward-engineering/) · [What is Forward Deployed Engineering](https://invisibletech.ai/blog/what-is-forward-deployed-engineering)

### Foundation Model

Ein großes, auf breiten Daten vortrainiertes Modell, das als gemeinsame Basis für viele nachgelagerte Aufgaben dient, statt für eine einzige trainiert zu sein. LLMs sind der bekannteste Fall; der Begriff umfasst aber auch Bild-, Audio- und multimodale Modelle.

**Einordnung:** Der Begriff stammt aus Stanford (2021) und betont die gemeinsame Grundlage, nicht die Größe. Oft synonym mit „Frontier Model" verwendet, das aber eher die jeweils leistungsstärkste Generation meint. Aus einem Foundation Model wird über Fine-Tuning oder RLHF ein einsatzfähiges Instruct-Modell.

**Mehr:** [Foundation model, Wikipedia](https://en.wikipedia.org/wiki/Foundation_model)

## G

### Grounding

Die Ausgabe wird an überprüfbare Quellen gebunden, statt sie allein aus dem Modellgedächtnis zu erzeugen. Übliche Umsetzungen sind RAG, Suchanbindung, Knowledge Graphs und Werkzeugaufrufe, oft verbunden mit einer Belegstelle je Aussage.

**Einordnung:** Grounding senkt die Rate erfundener Inhalte, es beseitigt sie nicht. Ein Modell kann eine korrekt abgerufene Quelle falsch zusammenfassen. Prüfbar wird das Ergebnis erst, wenn jede Aussage auf eine konkrete Stelle zeigt.

**Mehr:** [LLM Grounding, Glossareintrag](https://www.iguazio.com/glossary/llm-grounding/)

### Guardrail

Eine Kontrolle, die Ein- oder Ausgaben prüft und blockiert, filtert oder umleitet. Üblich sind Eingangsfilter gegen Prompt Injection, Ausgangsfilter gegen Datenabfluss und harte Grenzen für Rechte und Budgets.

**Einordnung:** Guardrails sitzen auf mehreren Ebenen gleichzeitig, nicht nur im Harness. Ein Guardrail, der als Anweisung im Prompt formuliert ist, ist eine Bitte an das Modell.

**Mehr:** [OWASP Top 10 for LLM Applications 2025, PDF](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf)

## H

### Hallucination

Das Modell erzeugt flüssigen, plausibel klingenden Inhalt, der falsch ist oder von den vorliegenden Quellen nicht gedeckt wird. Erfundene Zitate, Paragraphen, Bibliotheken und Personen sind die häufigsten Ausprägungen.

**Einordnung:** Das Wort legt eine Störung nahe. Tatsächlich ist es das Normalverhalten eines Systems, das wahrscheinliche Fortsetzungen erzeugt. Aus Modellsicht besteht kein Unterschied zwischen einer richtigen und einer erfundenen Antwort, weshalb sich das Verhalten begrenzen und messen, aber nicht wegreparieren lässt. In der OWASP-Liste als LLM09 Misinformation geführt.

**Mehr:** [Hallucination (artificial intelligence), Wikipedia](https://en.wikipedia.org/wiki/Hallucination_\(artificial_intelligence\))

### Harness

Die deterministische Laufzeitschicht um das Modell. Sie prüft, autorisiert, führt aus und protokolliert jede Aktion, die das Modell vorschlägt, gegen Schemata, Rechte, Budgets und Sicherheitsregeln.

**Einordnung:** Für die Qualitätssicherung die interessanteste Schicht, weil hier die Grenzen tatsächlich durchgesetzt werden. Was im Prompt steht, ist eine Bitte. Was im Harness steht, ist eine Regel.

**Mehr:** [Harness Engineering, Faros](https://www.faros.ai/blog/harness-engineering)

### Harness Engineering

Die Gestaltung der Laufzeitumgebung um das Modell herum. Produktive AI-Anwendungen erzeugen selten nur Text, sie führen Code aus, rufen Werkzeuge auf, suchen im Netz und prüfen Ergebnisse. Dazu gehören Tool Calling, MCP, Code-Ausführung, Browser-Automatisierung, Sub-Agents, Verifikation, Retry-Strategien, Fehlerbehandlung und Guardrails.

**Einordnung:** Seit 2026 breit im Umlauf, meist zusammengefasst als "Agent = Modell + Harness". Die Grenze zwischen Harness und Loop wird uneinheitlich gezogen, besonders bei Verifikation.

**Mehr:** [Harness Engineering, Faros](https://www.faros.ai/blog/harness-engineering) · [Harness Engineering for AI Coding Agents, Augment Code](https://www.augmentcode.com/guides/harness-engineering-ai-coding-agents)

### Human in the Loop

Ein Mensch bestätigt, korrigiert oder blockiert an definierten Stellen, bevor das System weiterläuft.

**Einordnung:** Wirksam gegen falsche Entscheidungen und wirkungslos, sobald niemand mehr hinsieht. Zwei Fallen: Freigabe-Ermüdung, bei der reflexhaft bestätigt wird, und Geschwindigkeit, denn in Abläufen, die auf Angriffe reagieren müssen, ist die Wartezeit auf einen Menschen selbst ein Risiko. Tragfähig wird das Muster, wenn vorab festgelegt ist, welche Aktionen eine Unterschrift brauchen, statt alle.

**Mehr:** [OWASP Top 10 for LLM Applications 2025, PDF](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf)

## I

### In-Context Learning

Die Fähigkeit eines Modells, eine Aufgabe allein aus Anweisungen und Beispielen im Prompt zu lösen, ohne dass seine Gewichte verändert werden. Mit mehreren Beispielen spricht man von Few-Shot, mit einem von One-Shot, ganz ohne von Zero-Shot.

**Einordnung:** Abzugrenzen vom Fine-Tuning: Hier lernt das Modell nichts dauerhaft, es nutzt nur den Kontext des aktuellen Aufrufs. Prompt Engineering ist im Kern die Kunst, dieses Verhalten gezielt auszulösen. Mehr Beispiele helfen, kosten aber Token und Platz im Context Window.

**Mehr:** [Language Models are Few-Shot Learners (GPT-3), Originalarbeit 2020](https://arxiv.org/abs/2005.14165)

## J

### Jailbreak

Eine Eingabe, die ein Modell dazu bringt, die ihm antrainierten Verhaltensgrenzen zu umgehen. Übliche Muster sind Rollenspiel, hypothetische Rahmung, Kodierung und das Fluten des Kontexts mit Beispielen.

**Einordnung:** Wird oft mit Prompt Injection in einen Topf geworfen. Der Jailbreak zielt auf die Richtlinie des Modells, die Prompt Injection auf die Anweisungshierarchie der Anwendung. Unterschiedliche Ziele, unterschiedliche Gegenmaßnahmen.

**Mehr:** [OWASP LLM Top 10, Übersicht bei Promptfoo](https://www.promptfoo.dev/docs/red-team/owasp-llm-top-10/)

## K

### Knowledge Graph

Wissen wird als Knoten und benannte Beziehungen abgelegt statt als Fließtext. Abfragen folgen den Kanten, wodurch sich mehrstufige Fragen beantworten lassen.

**Einordnung:** Stark dort, wo Beziehungen die eigentliche Information sind: Zuständigkeiten, Abhängigkeiten, Berechtigungen, Lieferketten. Der Aufwand liegt in Modellierung und Pflege, nicht in der Abfrage, weshalb solche Vorhaben eher an Organisation als an Technik scheitern.

## L

### LangChain

Ein Framework für den Bau von LLM-Anwendungen. Es liefert Bausteine für Modellaufrufe, Prompts, Werkzeuganbindung und Retrieval und vereinheitlicht die Schnittstellen verschiedener Anbieter.

**Einordnung:** Der bekannteste Vertreter seiner Art und entsprechend polarisierend. Die Abstraktionsschicht spart am Anfang Arbeit und erschwert später die Fehlersuche, weil zwischen eigenem Code und Modellaufruf mehrere Ebenen liegen. Für einfache Fälle genügt oft das SDK des Modellanbieters.

**Mehr:** [LangChain vs LangGraph vs LangSmith, Vergleich](https://www.truefoundry.com/blog/langchain-vs-langgraph-vs-langsmith)

### Langfuse

Offene, selbst betreibbare Plattform für Tracing und Evaluation von LLM-Anwendungen, unabhängig vom verwendeten Framework.

**Einordnung:** Die übliche Alternative zu LangSmith, wenn die Daten das eigene Netz nicht verlassen sollen. Im deutschen Umfeld häufig genau das Ausschlusskriterium.

**Mehr:** [langfuse.com](https://langfuse.com/)

### LangGraph

Aufsatz auf LangChain für Abläufe mit Zustand. Der Ablauf wird als Graph beschrieben, mit Zustandsführung, Checkpoints, Verzweigungen und Haltepunkten für menschliche Freigaben.

**Einordnung:** Deckt genau das ab, was hier unter Orchestration und Loop Engineering steht. Der Graph macht Abläufe prüfbar und verschiebt die Komplexität in die Graphdefinition.

**Mehr:** [LangChain vs LangGraph vs LangSmith, Vergleich](https://www.truefoundry.com/blog/langchain-vs-langgraph-vs-langsmith)

### LangSmith

Die kommerzielle Plattform desselben Anbieters für Tracing, Auswertung und Überwachung von LLM-Anwendungen. Über OpenTelemetry inzwischen auch für Anwendungen außerhalb von LangChain nutzbar.

**Mehr:** [LangChain vs LangGraph vs LangSmith, Vergleich](https://www.truefoundry.com/blog/langchain-vs-langgraph-vs-langsmith)

### Lethal Trifecta

Drei Eigenschaften, die zusammen den Abfluss vertraulicher Daten ermöglichen: Zugriff auf vertrauliche Daten, Verarbeitung unvertrauenswürdiger Inhalte und die Fähigkeit, nach außen zu kommunizieren. Der Begriff geht auf Simon Willison zurück, Juni 2025.

**Einordnung:** Die brauchbarste Schnellprüfung für Agenten-Architekturen. Zwei der drei Eigenschaften sind beherrschbar. Wer eine der drei entfernt, entfernt die gesamte Angriffsklasse, und meist ist der Ausgangskanal am einfachsten zu schließen.

**Mehr:** [The lethal trifecta for AI agents, Simon Willison](https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/)

### LLM-as-a-Judge

Ein Modell bewertet die Ausgabe eines anderen Modells anhand von Kriterien in natürlicher Sprache. Verbreitet dort, wo es keine eindeutig richtige Antwort gibt.

**Einordnung:** Der Judge ist selbst ein Messinstrument mit Fehlern und Schlagseite. Ohne Kalibrierung gegen menschliche Urteile ist sein Ergebnis eine Meinung mit Nachkommastellen.

**Mehr:** [Judging LLM-as-a-Judge, Originalarbeit 2023](https://arxiv.org/abs/2306.05685)

### Loop Engineering

Die Gestaltung der Frage, wann ein Agent weitermacht, neu ansetzt oder aufhört. Komplexe Aufgaben brauchen mehrere Durchgänge statt eines einzelnen Aufrufs. Dazu gehören Planung, Reflexion, Selbstkorrektur, Abbruchbedingungen, Iterationsgrenzen sowie Budgets für Zeit, Kosten und Token.

**Einordnung:** Ein vergleichsweise junger Begriff, aber etabliert genug, dass Anbieter wie IBM eigene Definitionen führen. Die Abbruchbedingung ist der Teil, der in der Praxis am häufigsten fehlt.

**Mehr:** [What Is Loop Engineering, IBM](https://www.ibm.com/think/topics/loop-engineering)

### Lost in the Middle

Der Effekt, dass Modelle Informationen am Anfang und Ende einer langen Eingabe zuverlässiger nutzen als in der Mitte. Relevante Inhalte, die mittig platziert sind, werden häufiger übersehen.

**Einordnung:** Ein Teileffekt von Context Rot, belegt in der Arbeit von Liu et al. (2023). Praktische Folge fürs RAG: Die besten Treffer gehören an den Rand des Prompts, nicht in die Mitte. Betrifft auch als „long-context" beworbene Modelle.

**Mehr:** [Lost in the Middle: How Language Models Use Long Contexts, 2023](https://arxiv.org/abs/2307.03172)

## M

### MCP (Model Context Protocol)

Ein offenes Protokoll, über das Modelle einheitlich an Werkzeuge, Datenquellen und Prompts angebunden werden. Es standardisiert, wie ein Client einem Modell verfügbare Werkzeuge beschreibt und deren Aufrufe abwickelt.

**Einordnung:** MCP ist eine Umsetzung von Tool Calling, kein eigenständiges Konzept daneben. Aus Sicherheitssicht relevant, weil ein MCP-Server eine Vertrauensgrenze verschiebt. Es gibt inzwischen eine eigene OWASP-Liste dafür. Von MCP stammt Anthropic, es ist mit Abstand das verbreitetste der Agentenprotokolle. Zur Abgrenzung gegen ACP und A2A siehe dort.

**Mehr:** [modelcontextprotocol.io](https://modelcontextprotocol.io/) · [OWASP MCP Top 10](https://owasp.org/www-project-mcp-top-10/)

### Memory

Speicher, der über eine einzelne Sitzung hinaus erhalten bleibt: Fakten über den Nutzer, frühere Entscheidungen, Arbeitsstände. Technisch meist eine Datei oder ein Vektorspeicher, aus dem bei Bedarf nachgeladen wird.

**Einordnung:** Memory ist Context Engineering mit Persistenz, kein Modellgedächtnis. Sicherheitsrelevant, weil eine einmal eingeschleuste Falschinformation die Sitzung überlebt. Was hineingeschrieben wird, gehört genauso geprüft wie eine Eingabe.

**Mehr:** [Effective context engineering for AI agents, Anthropic](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)

### Mixture of Experts (MoE)

Eine Architektur, in der ein Modell aus vielen spezialisierten Teilnetzen („Experten") besteht, von denen pro Token nur wenige aktiviert werden. So wächst die Parameterzahl, ohne dass die Rechenkosten je Token im gleichen Maß steigen.

**Einordnung:** Erklärt, warum große Modelle bei moderater Inferenzlast möglich sind. Ein Router entscheidet, welche Experten ein Token bearbeiten; genau dieses Routing trägt zur schwächeren Reproduzierbarkeit bei, siehe Determinism und Reproducibility. Nicht mit Model Routing zu verwechseln, das zwischen ganzen Modellen wählt, nicht innerhalb eines Modells.

**Mehr:** [Mixture of experts, Wikipedia](https://en.wikipedia.org/wiki/Mixture_of_experts)

### Model Drift und Upgrade-Regression

Das Verhalten einer Anwendung ändert sich, ohne dass ihr Code sich ändert, weil der Anbieter das Modell aktualisiert oder ersetzt. Prompts, die vorher zuverlässig trugen, liefern plötzlich andere Ergebnisse.

**Einordnung:** Model Drift stammt aus dem klassischen Machine Learning und meint dort veränderte Eingabedaten über die Zeit. Im LLM-Umfeld wird derselbe Begriff für den Modellwechsel selbst verwendet, also beim Lesen klären, welche Bedeutung gemeint ist. Aus QA-Sicht der stärkste Grund, überhaupt Evals zu betreiben: Ohne sie bemerkt den Unterschied niemand.

### Model Routing

Anfragen werden je nach Aufgabe an unterschiedliche Modelle geleitet, einfache an ein kleines und schnelles, schwierige an ein großes.

**Einordnung:** Spart Kosten und Latenz und erzeugt eine neue Testfrage. Das Verhalten der Anwendung hängt jetzt davon ab, welchen Weg der Router wählt, also braucht der Router eigene Testfälle.

### Model Supply Chain

Die Kette aus Modellgewichten, Trainings- und Feinabstimmungsdaten, Adaptern, Bibliotheken und Werkzeugservern, aus der eine AI-Anwendung zusammengesetzt ist. Jede Station ist eine Bezugsquelle mit eigenem Vertrauensproblem.

**Einordnung:** Gewichte sind Binärdateien aus fremder Hand, und manche Serialisierungsformate führen beim Laden Code aus. In der OWASP-Liste als LLM03 geführt. Der Vorfall bei Hugging Face im Juli 2026 begann in der Datenverarbeitungspipeline, nicht im Modell, was die Bandbreite dieser Angriffsfläche zeigt.

**Mehr:** [OWASP Top 10 for LLM Applications 2025, PDF](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf) · [Security incident disclosure, Hugging Face](https://huggingface.co/blog/security-incident-july-2026)

### Multi-Agent System

Mehrere Agenten arbeiten an derselben Aufgabe, entweder gleichrangig oder unter einem koordinierenden Agenten.

**Einordnung:** Klingt nach Arbeitsteilung, kostet aber Kontext, Latenz und Nachvollziehbarkeit. Häufig löst ein einzelner Agent mit besseren Werkzeugen dieselbe Aufgabe. Sicherheitsrelevant, weil sich Rechte über Agentengrenzen hinweg unbemerkt summieren können.

**Mehr:** [Building effective agents, Anthropic](https://www.anthropic.com/engineering/building-effective-agents)

## O

### Observability und Tracing

Aufzeichnung dessen, was ein System tatsächlich getan hat: Prompts, Modellantworten, Werkzeugaufrufe, Zwischenschritte, Latenzen, Kosten. Ein Trace verkettet diese Ereignisse zu einem nachvollziehbaren Lauf.

**Einordnung:** Bei nichtdeterministischen Systemen ersetzt die Aufzeichnung die Wiederholbarkeit. Ohne Trace ist ein Fehlerbericht wertlos, weil sich der Lauf nicht rekonstruieren lässt. Aus Datenschutzsicht heikel, weil ein vollständiger Trace sämtliche Eingaben enthält. Für die Vereinheitlichung gibt es die GenAI Semantic Conventions von OpenTelemetry, Stand Mitte 2026 noch im Entwurf.

**Mehr:** [OpenTelemetry GenAI Semantic Conventions](https://mlflow.org/docs/latest/genai/tracing/opentelemetry/genai-semconv/)

### Open Weight und Open Source

Open Weight heißt: Die Gewichte stehen zum Download bereit und lassen sich lokal ausführen. Open Source im strengen Sinn verlangt zusätzlich offene Trainingsdaten, offenen Trainingscode und eine Lizenz ohne Nutzungseinschränkungen.

**Einordnung:** Die meisten als Open Source beworbenen Modelle sind Open Weight mit Auflagen. Für die Praxis zählt vor allem, ob man sie auf eigener Hardware betreiben darf. Bei Forensik mit vertraulichen Daten gibt genau das den Ausschlag, weil weder Daten noch Zugangsdaten das eigene Netz verlassen.

**Mehr:** [Open Source AI Definition, Open Source Initiative](https://opensource.org/ai)

### Orchestration

Die Steuerung mehrerer Schritte, Modelle und Werkzeuge zu einem Ablauf, inklusive Reihenfolge, Parallelität, Zustandsführung und Fehlerbehandlung.

**Einordnung:** Wird oft mit Agent verwechselt. Orchestration legt den Ablauf vorab fest, ein Agent entscheidet ihn zur Laufzeit. Die meisten produktiven Systeme sind Mischformen aus beidem.

**Mehr:** [Building effective agents, Anthropic](https://www.anthropic.com/engineering/building-effective-agents)

### Orchestrator Agent

Der führende Agent im Orchestrator-Workers-Muster. Er zerlegt die Aufgabe, beauftragt Sub-Agents mit klar umrissenen Teilaufgaben, sammelt deren Ergebnisse ein und entscheidet über den nächsten Schritt. Anthropic nennt ihn in seiner Forschungsarchitektur Lead Agent.

**Einordnung:** Von der Orchestration zu unterscheiden: Dort steht der Ablauf im Code, hier entscheidet ein Modell zur Laufzeit. Die Worker sprechen nicht miteinander, jede Entscheidung über den nächsten Schritt liegt beim Orchestrator. Das Muster lohnt sich, wenn die Teilaufgaben vorab unbekannt sind. Sind sie bekannt, zahlt man Kontext, Latenz und Nachvollziehbarkeit ohne Gegenwert.

**Mehr:** [How we built our multi-agent research system, Anthropic](https://www.anthropic.com/engineering/multi-agent-research-system) · [Orchestrator-Workers, Anthropic Cookbook](https://github.com/anthropics/anthropic-cookbook/blob/main/patterns/agents/orchestrator_workers.ipynb)

## P

### Prompt

Der gesamte Text, den ein Modell für einen Aufruf erhält. In der Praxis setzt er sich zusammen aus System Prompt, Werkzeugbeschreibungen, Gesprächshistorie, abgerufenen Inhalten und der aktuellen Eingabe.

**Einordnung:** Umgangssprachlich meint Prompt oft nur die Nutzereingabe. Technisch ist es alles, was das Modell sieht. Der Unterschied fällt spätestens auf, wenn Kosten, Latenz oder Fenstergrenzen zur Sprache kommen.

**Mehr:** [Prompt Engineering Overview, Anthropic](https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/overview)

### Prompt Caching

Wiederkehrende Teile eines Prompts, etwa System Prompt und Werkzeugbeschreibungen, werden beim Anbieter zwischengespeichert und bei folgenden Aufrufen günstiger und schneller verarbeitet.

**Einordnung:** Wirkt nur auf ein unverändertes Präfix. Eine Änderung am Anfang entwertet den Cache für alles Nachfolgende, weshalb Variables ans Ende gehört. Bei Agenten, die denselben Vorspann hundertfach senden, der größte einzelne Kostenhebel.

### Prompt Engineering

Die Gestaltung eines einzelnen Modellaufrufs. Dazu gehören Rollenzuweisung, Instruktionen und Einschränkungen, Beispiele im Prompt (Few-Shot), erzwungene Ausgabeformate wie JSON und wiederverwendbare Prompt-Templates.

**Einordnung:** Einer der älteren Begriffe im Feld und der am häufigsten für das Ganze gehaltene: Prompt Engineering wird oft mit der gesamten Arbeit an AI-Systemen gleichgesetzt. Es verliert nicht an Bedeutung, wird aber nur zu einem Teil von etwas Größerem.

**Mehr:** [Prompt Engineering Overview, Anthropic](https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/overview)

### Prompt Injection

Angreifergesteuerter Text bringt das Modell dazu, Anweisungen zu befolgen, die vom Betreiber nie vorgesehen waren. Direkt heißt: Der Nutzer selbst schreibt sie in die Eingabe. Indirekt heißt: Sie stecken in Inhalten, die das Modell im Rahmen seiner Arbeit liest, etwa in einer Webseite, einer Mail, einem PDF, einer Datei im Repository oder einem Tool-Ergebnis.

**Einordnung:** Nummer eins der OWASP Top 10 für LLM-Anwendungen und ohne allgemeine Lösung, weil Anweisungen und Daten denselben Kanal teilen. Filter senken die Trefferquote, sie beseitigen die Klasse nicht. Die tragfähige Entwurfsannahme lautet: Jeder Inhalt, den das Modell liest, kann Anweisungen enthalten. Die indirekte Variante ist die gefährlichere, weil der Angreifer keinen Zugang zur Anwendung braucht.

**Mehr:** [OWASP Top 10 for LLM Applications 2025, PDF](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf) · [Prompt Injection, Artikelserie von Simon Willison](https://simonwillison.net/tags/prompt-injection/)

### Promptfoo

Ein offenes Werkzeug zum Testen und Bewerten von LLM-Anwendungen: Prompts und Modelle vergleichen, Evals gegen erwartete Ergebnisse fahren und Red-Teaming gegen Prompt Injection und Jailbreaks automatisieren.

**Einordnung:** Produkt, kein Konzept, hier als im Gespräch gängiger Begriff aufgenommen. Deckt zwei Dinge ab, die in diesem Glossar getrennt stehen: Eval und Red Team. Läuft lokal und ist framework-unabhängig.

**Mehr:** [promptfoo.dev](https://www.promptfoo.dev/)

## Q

### Quantization

Die Gewichte, teils auch Aktivierungen, eines Modells werden in einem gröberen Zahlenformat gespeichert, etwa 8 oder 4 Bit statt 16. Das senkt Speicherbedarf und Rechenkosten und macht große Modelle auf kleinerer Hardware lauffähig.

**Einordnung:** Der übliche Weg, ein Modell lokal oder günstig zu betreiben; verwandt mit Distillation, aber ohne erneutes Training. Zu aggressive Quantisierung kostet Genauigkeit, besonders an den Rändern der Verteilung. Gängige Verfahren sind GPTQ und AWQ.

**Mehr:** [Quantization concepts, Hugging Face](https://huggingface.co/docs/transformers/en/quantization/concept_guide)

## R

### RAG (Retrieval Augmented Generation)

Externes Wissen wird zur Laufzeit gesucht und in den Prompt gelegt, statt es ins Modell zu trainieren. Typisch sind eine Vektorsuche über zerlegte Dokumente und eine anschließende Auswahl der besten Treffer.

**Einordnung:** Die Qualität steht und fällt mit dem Retrieval, nicht mit dem Modell. Beim Testen lohnt es sich, beides getrennt zu bewerten.

**Mehr:** [Retrieval-Augmented Generation, Originalarbeit 2020](https://arxiv.org/abs/2005.11401)

### Reasoning Model

Ein Modell, das vor der Antwort eine längere interne Ableitung erzeugt und dafür mehr Rechenzeit einsetzt. Stark bei mehrschrittigen Aufgaben, Mathematik und Code.

**Einordnung:** Teurer und langsamer, und die interne Ableitung ist meist gekürzt oder gar nicht sichtbar. Sie ist außerdem keine verlässliche Erklärung dafür, wie die Antwort zustande kam, taugt also nicht als Nachweis gegenüber einem Prüfer.

### Red Team und Blue Team

Das Red Team greift an, um Schwächen zu finden, das Blue Team verteidigt und erkennt. Bei AI-Systemen umfasst Red Teaming zusätzlich das systematische Hervorlocken unerwünschten Modellverhaltens vor der Freigabe.

**Einordnung:** Beide Seiten verlagern sich gerade auf Agenten, und dabei entsteht eine Schieflage. Das angreifende Agentensystem ist an keine Nutzungsrichtlinie gebunden und fragt niemanden. Das verteidigende hängt an den Guardrails seines Anbieters und an Freigabeschritten. Bei gleicher Fähigkeit entscheidet die Taktrate.

**Mehr:** [Security incident disclosure, Hugging Face](https://huggingface.co/blog/security-incident-july-2026)

### Reranking

Nach der ersten Suche sortiert ein zweites, genaueres Modell die Treffer neu, bevor die besten in den Kontext wandern.

**Einordnung:** Rettet häufig Systeme, deren Vektorsuche zu grob trifft. Kostet Latenz und einen zusätzlichen Modellaufruf. Beim Messen lohnt es sich, den Recall der Suche und die Präzision des Rerankers getrennt zu betrachten.

### RLHF (Reinforcement Learning from Human Feedback)

Ein Trainingsverfahren, das ein Modell an menschlichen Präferenzen ausrichtet: Menschen bewerten Modellantworten, daraus entsteht ein Belohnungsmodell, gegen das das Modell weiter optimiert wird. Der übliche Weg von einem Basismodell zu einem instruierbaren Chat-Modell.

**Einordnung:** Prägt Ton und Verhalten stark, ist aber teuer und schwer reproduzierbar, weil menschliche Urteile schwanken. Varianten ohne menschliche Labels heißen RLAIF, ein leichteres Gegenstück ist DPO (Direct Preference Optimization).

**Mehr:** [Training language models to follow instructions (InstructGPT), Originalarbeit 2022](https://arxiv.org/abs/2203.02155) · [RLHF, Wikipedia](https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback)

## S

### Sampling

Das Verfahren, mit dem aus der Wahrscheinlichkeitsverteilung des Modells das nächste Token gezogen wird. Top-k beschränkt die Auswahl auf die k wahrscheinlichsten Token, Top-p (Nucleus) auf die kleinste Menge, deren Wahrscheinlichkeiten zusammen p ergeben.

**Einordnung:** Zusammen mit Temperature und Seed der Hebel für Vielfalt gegen Vorhersagbarkeit. Greedy Decoding, also immer das wahrscheinlichste Token, klingt sicher, erzeugt aber oft flache, repetitive Texte, weshalb Top-p heute Standard ist. Wirkt nur bei Temperature über 0.

**Mehr:** [The Curious Case of Neural Text Degeneration (Nucleus Sampling), 2019](https://arxiv.org/abs/1904.09751)

### Sandbox und Containment

Die Sandbox begrenzt, was auf Veranlassung des Modells ausgeführter Code erreichen kann: Dateisystem, Netzwerk, Zugangsdaten, Rechen- und Zeitbudget. Containment ist die übergeordnete Eigenschaft, dass Aktionen die vorgesehene Grenze nicht verlassen.

**Einordnung:** Eine Sandbox ist so stark wie ihr großzügigster erlaubter Ausgang. Im Vorfall bei OpenAI und Hugging Face im Juli 2026 genügte ein freigegebener Paket-Proxy, um aus einer als isoliert geltenden Umgebung ins offene Netz zu gelangen.

**Mehr:** [OpenAI zum Vorfall](https://openai.com/index/hugging-face-model-evaluation-security-incident/) · [Technische Timeline, Hugging Face](https://huggingface.co/blog/agent-intrusion-technical-timeline)

### Sandboxed Code Execution

Vom Modell erzeugter Code wird ausgeführt, aber in einer abgeschotteten Umgebung mit begrenztem Zugriff auf Dateisystem, Netzwerk, Zugangsdaten und Laufzeit.

**Einordnung:** Der Standardweg, Codeausführung überhaupt zu erlauben, und gleichzeitig die Stelle, an der Containment üblicherweise scheitert. Der Fluchtweg ist selten die Sandbox selbst, sondern ein bewusst freigegebener Ausgang wie ein Paket-Proxy oder ein Registry-Spiegel.

**Mehr:** [OpenAI zum Vorfall](https://openai.com/index/hugging-face-model-evaluation-security-incident/)

### Shadow AI

Der Einsatz von AI-Tools durch Mitarbeitende ohne Freigabe oder Kenntnis der IT- und Sicherheitsabteilung, etwa das Einspeisen von Firmendaten in einen öffentlichen Chatbot. Eine Spielart von Shadow IT, zugespitzt auf AI-Werkzeuge und -Agenten.

**Einordnung:** Das Hauptrisiko ist Datenabfluss in externe Dienste, dazu ungeprüfte Ausgaben in Arbeitsergebnissen. Verbote verschieben das Problem meist nur; wirksamer ist ein freigegebener, gut nutzbarer Ersatz. Abzugrenzen von Shadow IT, das jede nicht freigegebene Software meint, nicht nur AI.

**Mehr:** [What Is Shadow AI?, IBM](https://www.ibm.com/think/topics/shadow-ai)

### Skill

Ein verpacktes Bündel aus Instruktionen und optional Skripten oder Ressourcen, das ein Modell bei Bedarf nachlädt, um eine bestimmte Art von Aufgabe zu erledigen.

**Einordnung:** Anthropic führt das Konzept als Agent Skills, ein Ordner aus Instruktionen, Skripten und Ressourcen, den Claude bei passender Gelegenheit selbst lädt. Leicht mit Tool oder Prompt-Template zu verwechseln. Das unterscheidende Merkmal ist der bedingte Nachladevorgang, weshalb ein Skill in erster Linie ein Mittel des Context Engineering ist. Sobald ausführbare Skripte dazugehören, reicht er in den Harness hinein.

**Mehr:** [Agent Skills, Claude Platform Docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) · [Offene Skills-Sammlung, Anthropic](https://github.com/anthropics/skills)

### Structured Output

Das Modell wird auf ein festgelegtes Ausgabeformat verpflichtet, meist JSON gegen ein Schema. Umgesetzt entweder durch eingeschränktes Decoding oder durch nachgelagerte Validierung mit Wiederholung.

**Einordnung:** Schemakonformität ist keine inhaltliche Richtigkeit. Ein gültiges JSON kann falsche Werte enthalten. Der eigentliche Gewinn liegt darin, dass sich die Ausgabe maschinell weiterverarbeiten und damit überhaupt automatisch prüfen lässt.

### Sub-Agent

Ein eigener Agent mit eigenem Kontext, an den ein übergeordneter Agent eine Teilaufgabe abgibt. Er liefert ein Ergebnis zurück, ohne seinen gesamten Arbeitsverlauf mitzubringen.

**Einordnung:** Nützlich zur Entlastung des Context Window, weil der Sub-Agent in einem frischen Kontext arbeitet und nur das Ergebnis zurückgibt. Der Preis ist, dass der übergeordnete Agent nur die Zusammenfassung sieht und Fehler im Detail schwerer bemerkt. Der Gegenpart ist der Orchestrator Agent, bei Anthropic Lead Agent genannt.

**Mehr:** [Building effective agents, Anthropic](https://www.anthropic.com/engineering/building-effective-agents)

### System Prompt

Die Instruktionen, die vor dem eigentlichen Gespräch stehen und Rolle, Regeln, Ton und verfügbare Werkzeuge festlegen. Sie gelten über alle Züge hinweg und stammen vom Betreiber der Anwendung, nicht vom Nutzer.

**Einordnung:** Keine Sicherheitsgrenze. Der System Prompt liegt im selben Context Window wie alles andere und konkurriert mit späterem Text um Aufmerksamkeit. Er lässt sich in der Regel auslesen, also gehören Geheimnisse dort nicht hinein. In der OWASP-Liste als LLM07 System Prompt Leakage geführt.

**Mehr:** [OWASP Top 10 for LLM Applications 2025, PDF](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf)

## T

### Temperature und Seed

Temperature skaliert die Wahrscheinlichkeitsverteilung, bevor das nächste Token gezogen wird. Niedrige Werte machen die Auswahl vorhersehbarer, hohe Werte vielfältiger. Der Seed setzt den Startwert des Zufallsgenerators beim Sampling.

**Einordnung:** Bei Temperature 0 wird rechnerisch stets das wahrscheinlichste Token gewählt, womit der Seed wirkungslos wird. Eine identische Ausgabe garantiert das trotzdem nicht, siehe Determinism und Reproducibility. Einen Seed bieten zudem nicht alle Anbieter an.

**Mehr:** [Controlling randomness in LLMs: Temperature and Seed](https://dylancastillo.co/posts/seed-temperature-llms.html)

### Token

Die kleinste Einheit, in die Text zerlegt wird, bevor ein Modell ihn verarbeitet. Ein Token entspricht grob einem Wortteil.

**Einordnung:** Kosten, Latenz und die Grenze des Context Window rechnen alle in Token, nicht in Zeichen oder Wörtern. Deutsche Texte brauchen für denselben Inhalt spürbar mehr Token als englische, was Budgets und Fenstergrenzen verschiebt.

**Mehr:** [Tokenizer zum Ausprobieren, OpenAI](https://platform.openai.com/tokenizer)

### Token Budget

Eine Obergrenze für Token je Aufruf, je Lauf oder je Zeitraum. Dient der Kostenkontrolle und zugleich als Abbruchbedingung gegen endlose Schleifen.

**Einordnung:** Eine der wenigen Grenzen, die sich hart durchsetzen lassen, weil sie über Inhalte nichts annehmen muss. Sie gehört deshalb in den Harness und nicht in den Prompt.

### Tool Calling

Das Modell gibt statt Text einen strukturierten Aufruf aus, den die umgebende Software ausführt. Das Ergebnis kommt als neue Information zurück in den Kontext.

**Einordnung:** Das Modell ruft nichts auf, es schlägt einen Aufruf vor. Wer ausführt und mit welchen Rechten, ist eine Architekturentscheidung.

**Mehr:** [Building effective agents, Anthropic](https://www.anthropic.com/engineering/building-effective-agents)

### Tool Poisoning

Schädliche Anweisungen stecken in den Beschreibungen von Werkzeugen, also in Namen, Dokumentation und Parameterbeschreibungen, die das Modell als Teil seines Kontexts liest. Relevant überall dort, wo Werkzeugdefinitionen von fremden Servern kommen.

**Einordnung:** Wirksam, weil Werkzeugbeschreibungen praktisch nie gelesen und geprüft werden. Dazu kommt, dass ein Server seine Beschreibungen nach der Freigabe ändern kann, was als Rug Pull bezeichnet wird. Als Gegenmaßnahme bietet sich an, die Definition nach der Prüfung einzufrieren.

**Mehr:** [MCP03:2025 Tool Poisoning, OWASP](https://owasp.org/www-project-mcp-top-10/2025/MCP03-2025%E2%80%93Tool-Poisoning) · [Reproduzierbare Beispiele, Invariant Labs](https://github.com/invariantlabs-ai/mcp-injection-experiments)

## V

### Vector Database

Eine Datenbank, die auf das Speichern und schnelle Durchsuchen von Embeddings ausgelegt ist. Sie findet zu einem Anfrage-Vektor die nächstgelegenen Einträge, meist über angenäherte Nachbarschaftssuche (ANN).

**Einordnung:** Das Rückgrat der meisten RAG-Systeme und die technische Heimat von Memory. Der eigentliche Aufwand liegt selten in der Datenbank, sondern in Chunking, Embedding-Wahl und Reranking davor und danach. Bekannte Vertreter sind Pinecone, Weaviate, Qdrant und Chroma; klassische Datenbanken bieten Vektor-Suche inzwischen als Zusatz.

**Mehr:** [Vector database, Wikipedia](https://en.wikipedia.org/wiki/Vector_database)

### Vector Search

Suche über Embeddings: Die Anfrage wird in denselben Vektorraum übersetzt, dann werden die nächstgelegenen Einträge zurückgegeben.

**Einordnung:** Findet Ähnliches, nicht Richtiges. Bei exakten Bezeichnern, Versionsnummern, Fehlercodes und Fachbegriffen schlägt klassische Volltextsuche sie regelmäßig, weshalb Hybridverfahren aus beidem heute üblich sind.

**Mehr:** [Why Vector Search Alone Isn't Enough, InfoQ](https://www.infoq.com/articles/vector-search-hybrid-retrieval-rag/)

### Vibe Coding

Programmieren durch Beschreiben: Man schildert in natürlicher Sprache, was entstehen soll, übernimmt den erzeugten Code weitgehend ungelesen und steuert über weitere Beschreibungen nach. Der Begriff geht auf Andrej Karpathy zurück, Februar 2025.

**Einordnung:** Für Wegwerfarbeit, Prototypen und Erkundung eine tragfähige Arbeitsweise. Der Punkt, der die Methode definiert, ist der weggelassene Review-Schritt, und genau der entscheidet darüber, ob das Ergebnis in Produktion darf. Der Begriff wird inzwischen häufig einfach für "Entwickeln mit AI-Unterstützung" verwendet, was ihn unbrauchbar macht.

**Mehr:** [Vibe coding, Wikipedia](https://en.wikipedia.org/wiki/Vibe_coding)

## W

### Workflow

Eine festgelegte Abfolge von Schritten, in der Reihenfolge und Verzweigungen im Code stehen. Modellaufrufe sind einzelne Stationen darin.

**Einordnung:** Der Gegenbegriff zum Agentic Workflow. Ein Workflow ist vorhersehbar, prüfbar und langweilig, was in der Produktion drei Vorteile sind. Viele als agentisch verkaufte Systeme sind Workflows, und meistens ist das die richtige Wahl.

**Mehr:** [Building effective agents, Anthropic](https://www.anthropic.com/engineering/building-effective-agents)
