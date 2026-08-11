# Style Guide — aiGlossar
 
Die einzige verbindliche Quelle dafür, wie ein Eintrag aussieht. `README.md` und
`CLAUDE.md` verweisen hierher, statt Regeln zu wiederholen. Duplikate driften
auseinander.
 
## Grundsätze
 
**Definition knapp, Einordnung wertvoll.** Die Definition ist Handwerk und steht
so ähnlich überall. Der Wert dieses Glossars ist die Einordnung: wie fest ein
Begriff sitzt, wo er uneinheitlich verwendet wird, womit man ihn verwechselt.
 
**Englischer Begriff, deutsche Erklärung.** Die Begriffe werden im Arbeitsalltag
englisch gesprochen und bleiben englisch. Erklärt wird auf Deutsch.
 
**Beschreiben, nicht vorschreiben.** Das Glossar hält fest, wie Begriffe
verwendet werden, auch wenn die Verwendung uneinheitlich ist. Es legt nicht fest,
wie sie verwendet werden sollten.
 
**Datiert statt endgültig.** Ein Eintrag ist ein Messpunkt mit Datum. Verschiebt
sich eine Bedeutung, kommt der neue Stand dazu, statt den alten zu ersetzen.
 
**Wo Hersteller abweichen, gilt Anthropic.** Abweichende Bezeichnungen anderer
Anbieter kommen in die Einordnung.
 
## Anatomie eines Eintrags
 
In dieser Reihenfolge, jeweils durch eine Leerzeile getrennt:
 
1. **Begriff** als `###`-Überschrift. Englischer Fachbegriff im Singular, bei
   Abkürzungen mit Ausschreibung in Klammern: `### MCP (Model Context Protocol)`.
2. **Definition.** Zwei bis drei Sätze, höchstens vier. Kein Fachjargon zum
   Erklären von Fachjargon.
3. **Einordnung**, eingeleitet mit `**Einordnung:**`. Höchstens fünf Sätze.
4. **Mehr**, eingeleitet mit `**Mehr:**`. Optional. Mehrere Links mit ` · `
   getrennt.
Es gibt kein Kategorie-Tag, keine `Siehe auch:`-Zeile und keine Aufzählungen
innerhalb eines Eintrags.
 
### Wann die Einordnung entfällt
 
Nur wenn alle drei Punkte zutreffen: Der Begriff ist stabil, eindeutig belegt und
nicht mit einem anderen verwechselbar. Alles andere bekommt eine Einordnung.
 
### Wann die Mehr-Zeile entfällt
 
Wenn es keine belastbare herstellerneutrale Quelle gibt, die über die Definition
hinausgeht. Das Weglassen ist eine Aussage, kein Versäumnis, und die README
erklärt das den Lesern.
 
## Bedeutungsverschiebungen
 
Der Kern des Projekts. Wenn sich die Verwendung eines Begriffs nachweislich
verschoben hat, kommt in die Einordnung eine eigene Zeile:
 
```md
**Verschiebung:** Bis Mitte 2025 bezeichnete der Begriff überwiegend X.
Seit 2026 wird er für Y verwendet.
```
 
Der alte Stand bleibt stehen. Wer wissen will, was jemand 2025 mit dem Wort
meinte, findet es hier. Einzelne Einträge tragen kein eigenes Datum, das
Dokument trägt oben ein `Stand:`, das bei jeder Durchsicht aktualisiert wird.
 
## Struktur und Sortierung
 
- Das Glossar ist **flach alphabetisch** von A bis Z, nicht thematisch.
- Jeder belegte Anfangsbuchstabe ist ein Abschnitt `## A`, `## B` und so weiter.
  Fehlt der Buchstabe, wird der Abschnitt an der richtigen Stelle angelegt.
- Sortiert wird nach dem Begriff ohne Klammerzusatz und ohne Beachtung der
  Groß- und Kleinschreibung. `MCP (Model Context Protocol)` steht unter `M`.
- Ganz oben steht eine Buchstabennavigation, die beim Anlegen eines neuen
  Buchstabens ergänzt wird.
- Anker erzeugt GitHub automatisch aus der Überschrift. Sie werden nicht von
  Hand gepflegt.
## Querverweise
 
Verweise auf andere Einträge stehen im Fließtext der Definition oder Einordnung,
etwa „siehe Context Rot" oder „zur Abgrenzung siehe dort". `**Mehr:**` ist
ausschließlich für externe Quellen.
 
## Sprache und Schreibweise
 
- **Keine Gedankenstriche.** Weder Halbgeviert noch Geviert. Stattdessen Punkt,
  Komma, Doppelpunkt, Klammer oder zwei Sätze.
- **Positiv formulieren.** Beschreiben, wie etwas ist, statt wie es nicht ist.
  Keine Häufung von „nicht" und „kein".
- **Sachlich.** Keine Wertungen, keine Superlative, keine Marketingsprache.
- Deutsche Anführungszeichen „…" im Fließtext.
- Fette Beschriftungen für `**Einordnung:**` und `**Mehr:**`, kein Kursiv.
## Quellen
 
- Herstellerneutral und primär bevorzugt: OWASP, arXiv-Originalarbeiten,
  offizielle Spezifikationen, Wikipedia. Vor Marketing-Blogs.
- Stammt ein Konzept von einem Anbieter, etwa MCP von Anthropic, ist dessen
  Primärquelle in Ordnung.
- Keine Quelle erfinden. Im Zweifel die Mehr-Zeile weglassen.
- Bei jeder Durchsicht werden die Links geprüft. Tote Links werden ersetzt oder
  entfernt, nicht stehen gelassen.
## Was rein gehört
 
Begriffe aus dem Arbeitsalltag mit AI-Systemen: Modelle, Training, Inferenz,
Architektur, Agenten, Retrieval, Sicherheit, Qualität und Messung. Auch Begriffe,
die älter sind als Sprachmodelle und neu angewendet werden, etwa Confused Deputy
von 1988.
 
## Was nicht rein gehört
 
- Allgemeine IT-Begriffe ohne AI-Bezug.
- Meinungen, Wertungen, Marketingsprache.
- Essays und Code-Tutorials. Dafür verlinken.
- Produkte und Anbieter sind die bewusste Ausnahme: nur aufnehmen, wenn der Name
  im Gespräch als Begriff auftaucht, in der Einordnung klar als Produkt
  kennzeichnen und Marktangaben sparsam halten. Sie veralten schneller als
  Definitionen.
## Zweisprachigkeit
 
`GLOSSAR_DE.md` ist die Quelle, `GLOSSAR_EN.md` die Übersetzung. Änderungen
gehen zuerst nach DE. Ein Eintrag gilt erst als fertig, wenn beide Fassungen
ihn enthalten. Die englische Fassung folgt denselben Regeln, mit englischer
Erklärung und den Beschriftungen `**Assessment:**` und `**More:**`.
 
## Template
 
```md
### Begriff (Ausschreibung)
 
Zwei bis drei Sätze Definition auf Deutsch. Sachlich, ohne Bewertung.
 
**Einordnung:** Wie fest sitzt der Begriff, wo wird er uneinheitlich verwendet,
womit ist er zu verwechseln. Verweise auf andere Einträge hier im Fließtext.
 
**Mehr:** [Quelle](https://…) · [Weitere Quelle](https://…)
```
 
## Beispiele
 
**Gut:**
 
```md
### Grounding
 
Die Ausgabe wird an überprüfbare Quellen gebunden, statt sie allein aus dem
Modellgedächtnis zu erzeugen. Übliche Umsetzungen sind RAG, Suchanbindung und
Werkzeugaufrufe, oft mit einer Belegstelle je Aussage.
 
**Einordnung:** Grounding senkt die Rate erfundener Inhalte, es beseitigt sie
nicht. Ein Modell kann eine korrekt abgerufene Quelle falsch zusammenfassen.
 
**Mehr:** [LLM Grounding, Glossareintrag](https://www.iguazio.com/glossary/llm-grounding/)
```
 
Englischer Begriff, drei Sätze Definition, eine Einordnung, die die Grenze des
Konzepts benennt, Querverweis im Fließtext, herstellerneutrale Quelle.
 
**Schlecht:**
 
```md
### Das beste Grounding-Tool
*Kategorie: Qualität*
 
Grounding ist super wichtig und jeder braucht es. Man nimmt am besten Produkt X,
klickt auf Einrichten, wählt die Datenquelle, dann …
 
Siehe auch: [RAG](#rag)
```
 
Wertende Überschrift statt Begriff, verbotenes Kategorie-Tag, Meinung,
Produktwerbung und Tutorial statt Definition, keine Einordnung, `Siehe auch:`
statt Verweis im Fließtext.
 