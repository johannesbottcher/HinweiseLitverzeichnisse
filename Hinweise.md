Wissenschaftliches Arbeiten beinhaltet auch das belegen
verwendeter Literatur in Form von Literaturangaben sowie
ordentlichen Literaturverzeichnissen. Das Literaturverzeichnis
muss laut [Schenk (Seite 92)][schenk] folgenden
*Anforderungen* entsprechen:

- Richtigkeit
- Vollständigkeit
- Einheitlichkeit
- Übersichtlichkeit
- Ehrlichkeit

LaTeX als Textsatzprogramm kann hier unterstützen, jedoch trägt
der Autor selbst für die Einhaltung der oben genannten Punkte
Verantwortung.

**Literaturverzeichnisse mit LaTeX**
=========================



*Für die Erstellung von Literaturverzeichnissen mit LaTeX ist in
diesen Tagen das moderne Paket [biblatex](www.ctan.org/pkg/biblatex)
in Verbindung mit dem Bibliographieprozessor
[biber](www.ctan.org/pkg/biber) sehr empfehlenswert. Pakete wie natbib
oder cite in Verbindung mit BibTeX oder sogar das manuelle Erstellen
des Verzeichnisses, gelten als veraltet.*



Der schnelle Umstieg für erfahrene Benutzer
-----------------

Biblatex und biber sind ein großartiges Team. Biblatex bietet eine
Auswahl vordefinierter Stile für Zitationen und Bibliographien, welche
auch leicht [geändert werden
können](http://texwelt.de/blog/modifizieren-eines-biblatex-stils/).
Die [biblatex-Support-Seite](http://www.ctan.org/topic/biblatex) auf
[CTAN](http://www.ctan.org) liefert zusätzliche Stile. Der
moderne Bibliographieprozessor biber [bietet einige Vorteile gegenüber dem
konventionellen
BibTeX](http://texwelt.de/wissen/fragen/5398/was-sind-die-vorteile-von-biber-gegenuber-bibtex).
Für erfahrene LaTeX-Nutzer, welche den Umstieg auf LyX gewagt haben,
gibt es auch gute Nachrichten, denn [LyX und biblatex vertragen
sich](http://texwelt.de/wissen/fragen/2768/biblatex-und-biber-mit-lyx/2847).


`biblatex` selbst bietet viele Möglichkeiten und ersetzt eine
Reihe von Paketen welche im Zusammenhang mit dem klassischen
BibTeX gebraucht wurden.  Da `biblatex` mit LaTeX-Dateien zur
Stilbeschreibung arbeitet, ist der Befehl `\bibliographystyle`
nicht mehr nötig. Stattdessen wird der Bibliographiestil als
Paketoption übergeben (`style=authoryear`).  Bereits existierende
BibTeX-Datenbanken sind kompatibel, können aber um weitere
Eintragstypen und -felder erweitert werden. Ein höheres Maß an
Flexibilität ist so möglich. Der Name der Datenbank wird mit dem
Befehl `\addbibresource` übergeben. Da verschiedene Formate
gültig sind, ist die Angabe der Dateiendung nötig. 

Wie gewohnt wird mit dem Befehl `\cite{bib-key}` zitiert,
`biblatex` bietet aber auch Alternativen. Mit `autocite` kann
global das Erscheinungsbild der Zitationen im Text geändert
werden. Auch Befehle wie `citetitle`, `citeyear` und ähnliche
sind sehr nützlich. 

Im Dokument wird das Literaturverzeichnis mit `\printbibliography`
ausgegeben. Der Befehl kennt optionale Argumente, beispielsweise um
den Titel anzupassen oder das Verzeichnis auf bestimmte Eintragstypen
zu beschränken. 

Dabei ist die allgemeine Arbeitsweise mit dem älteren System
kompatibel. Das bedeutet der Rhythmus `latex`, `biber`/`bibtex`,
`latex`, `latex` bleibt erhalten. 

-------------------------------------------------------------


Einstieg in die Literaturverwaltung mit biblatex
-------------------------------------------

Wer noch nie ein Literaturverzeichnis mit LaTeX erstellt hat, sollte
sich zu Beginn mit einigen Grundlagen vertraut machen. Hier soll nur
ein kurzer Überblick gegeben werden, welcher allerdings noch
keinen tiefgründigen Einblick liefert. Wer in ein gutes Fundament
investiert, hat später weniger Ärger. Ein Blick in die genannte
Literatur ist also  lohnenswert.


### DIY - Do it yourself

Es ist zwar möglich das Literaturverzeichnis von Hand zu
erstellen, schließlich ist ein Literaturverzeichnis nur eine
Liste, aber wer will das schon. Genaueres findet sich bei
Interesse in der
[LaTeX2ε-Kurzbeschreibung][l2kurz], in
	Kapitel 5.6 von Nicola Talbots [LaTeX for Complete
Novices][novice]
oder auch in Kapitel 7 des
[LaTeX Beginner's Guide][stefan]
von Stefan Kottwitz. Bei sehr kurzen Verzeichnissen kann der
manuelle Ansatz noch vertretbar sein.

### Datenbanken - Infos auf der hohen Kante

Egal ob man sich für die Moderne entscheidet, oder verstaubtes
Handwerk auferstehen lässt, Grundlage effizienten Arbeitens ist
eine Datenbank mit allen nötigen und vielleicht auch unnötigen
Informationen. Im Bereich LaTeX üblich sind Datenbanken im
BibTeX-Format, reine (Text-)Dateien mit der
Endung *bib*. Jeder Eintrag hat folgende Form:

    @Eintragstyp{Keyword,  
    <feld name> = "<Text>",  
      .  
      .  
      .  
    <feld name> = "<text>",  
    }  

Ein Eintrag besteht aus einem *Keyword* (Bib-Key,
*Schlüsselwort*) mit welchem die Referenz auch im Dokument
angesprochen wird. Dieses Schlüsselwort sollte möglichst nur aus
Buchstaben des lateinischen Basisalphabets und Zahlen bestehen.
Satzzeichen wie Bindestriche und/oder Doppelpunkte können jedoch
sparsam eingesetzt werden. Informationen werden an die
jeweiligen Felder übergeben. Je nach Eintragstyp (`book`,
`online` etc.) können verschiedene Felder benötigt werden.
Eigene Felder können beliebig hinzugefügt werden.

Namen werden in BibTeX-Datenbanken durch das englische Wort *and*
getrennt, Namensteile hingegen werden durch Kommas abgetrennt.
Dies sollte man bereits bei der Eingabe beachten um späterer
Verwirrung vorzubeugen. Anbei ein kleines Beispiel.

    %MeineLiteratur.bib
    @book{aristotle:physics,
     author    = {Aristotle},
     title    = {Physics},
     date     = 1929,
     translator  = {Wicksteed, P. H. and Cornford, F. M.},
     publisher  = {G. P. Putnam},
     shorttitle  = {Physics},
    }
    
    @book{wilde,
     author    = {Wilde, Oscar},
     title    = {The Importance of Being Earnest: A Trivial
    Comedy for Serious People},
     year     = 1899,
     series    = {English and American drama of the Nineteenth
    Century},
     publisher  = {Leonard Smithers and Company},
    }

### Datenbanken verwalten

Das plattformunabhängige und kostenfreie [JabRef][jabref]
eignet sich gut für die Verwaltung von Literaturdatenbanken.
Beispiele zur Anwendung  finden sich bei [Talbot][thesis] und
[Voß][herbert].
[Citavi](http://citavi.de/de/index.html) kann bib-Dateien
exportieren, arbeitet aber intern mit einem anderen Format, es
kann daher zu Komplikationen kommen.

Oftmals kann man sich Schreibarbeit ersparen, denn Anbieter
elektronischer Medien stellen häufig einen BibTeX-Eintrag zur
Verfügung (ob dieser allerdings korrekt ist, ist eine andere Frage).

Grundlegende Informationen zu BibTeX-Datenbanken und möglichen
Stolperfallen bei der Eingabe bieten [Bibliografien mit
LaTeX][herbert] von Herbert Voß und [Using LaTeX to Write a PhD Thesis][thesis]
von Nicola Talbot.


### Erste Schritte mit biblatex

Im folgenden Minimalbeispiel laden wir das Paket `biblatex` und
geben mit `\addbibresource` Auskunft über den Namen der
bib-Datei. Ein Eintrag der Datenbank wird mit dem Befehl `\cite`
zitiert, Argument ist der Bib-Key (auch eine durch Kommata
getrennte Liste von Bib-Keys ist möglich). Das
Literaturverzeichnis wird durch `\printbibliography` ausgegeben.

    \documentclass{article}
    \usepackage{biblatex}
    \addbibresource{MeineLiteratur.bib}
    \begin{document}
    
    \parencite{aristotle:physics}
    \cite{wilde}
    \printbibliography
    \end{document} 



![citekey][citekey]

Nach dem ersten Lauf von LaTeX erhalten wir nicht ganz das
gewünschte Ergebnis, unsere Bibkeys stehen hässlich und fett im
Text. In der Log-datei ([Was sind
Hilfsdateien?](http://texwelt.de/wissen/fragen/2530/was-sind-hilfsdateien-und-wo-finde-ich-diese))
findet sich folgende Warnung:

    Package biblatex Warning: Please (re)run Biber on the file:
    (biblatex)        Minimalbeispiel 
    (biblatex)        and rerun LaTeX afterwards. 


Biber ist der Name des Hilfsprogramms, welches von `biblatex` für
die Sortierung der Referenzen genutzt wird.  Biber wird parallel
zu biblatex entwickelt, deshalb sollten beide auf dem neuesten
Stand sein.  Dies geht ganz leicht mit dem Paketmanager der
jeweiligen Distribution (tlmgr oder MikTeX Package manager).
Biber ist als Hilfsprogramm von LaTeX unabhängig und muss extra
aufgerufen werden; unter MikTeX 64-Bit sogar extra installiert
werden.  Beispiele zum Aufruf  für  verschiede Editoren finden sich unter »[Wie rufe ich
biber in meinem Editor auf?](www.texwelt.de/wissen/fragen/1909)«.
Möchte man stattdessen in einer
[Eingabeaufforderung/Terminal](http://texwelt.de/wissen/fragen/3461/wie-kompiliere-ich-in-der-eingabeaufforderung-im-terminal)
arbeiten, so lautet der Befehl `biber
hauptdokumentNameOhneDateiendung`. 

Biber sortiert nun und
schreibt anschließend einige Dateien. Das sind zum einen eine
Protokolldatei (`blg`), welche für eine eventuelle Fehlersuche
wichtig ist (»[Wie überprüfe ich, ob biber aufgerufen
wurde?](www.texwelt.de/wissen/fragen/2308)«) und die Datei,
welche beim erneuten Aufruf von `latex` verarbeitet wird um die
tatsächliche sortierte  Bibliographie und alle Referenzen zu setzen. 

Aus dem letzten Satz können wir schlussfolgern, dass wir LaTeX
erneut aufrufen müssen. Ergebnis unserer *Mühen* ist eine
numerische Zitation der Einträge (Zahl in eckigen Klammern) und ein sauberes
Literaturverzeichnis.

![numerische Zitation][numeric]

Bereits im Vorspann wurde erwahnt, dass biblatex verschiedene
Stile definiert. So kann man beim Laden des Paketes mit   
`\usepackage[style=authoryear]{biblatex}`  
die in den Geisteswissenschaften sehr übliche Zitation des Stils
Autor-Jahr wählen.  Natürlich können wir auch andere Stile
vorgeben, beispielsweise `style=authoryear` über Optionen beim
Laden des Paketes. Biblatex Weitere Stile, teilweise spezielle
Anpassungen an Verlagsvorlagen, werden durch
[Zusatzpakete](www.ctan.org/topic/biblatex) zur Verfügung
gestellt. 

Das Paket `biblatex` bietet eine Auswahl verschiedener
Zitierbefehle, verwendet man grundsätzlich `autocite`, kann man
sich global für eine gültige Zitationsweise entscheiden.  
Auch Befehle wie `\citeyear` oder `\citetitle` sind für viele
Nutzer ein großer Komfort. 

Nicht zu vergessen bleiben dew optionalen Argumente des
`\cite`-Befehls, mit welchem wir *pre*- und *postnotes* angeben
können.  Ausführlicher wird dies in der bereits erwähnten
Literatur beschrieben.

Die zuverlässigsten Informationen zu `biblatex` finden sich
allerdings in der Paketdokumentation des Pakets. Auch eine nicht
ganz aktuelle deutsche Übersetzung ist verfügbar.


Troubleshooting
--------------


Viele Nutzer stoßen beim Umstieg auf biblatex und biber auf das
ein oder andere Problem. Im Allgemeinen sind diese schnell zu
lösen.  
Läuft biber zum ersten mal, erhält man eventuell eine Meldung
wie:  
`[150] Utils.pm:167> WARN - Warning: Found biblatex control
file version 2.5, expected version 2.3 ` Das bedeutet schlicht,
dass die Versionen von biber und biblatex nicht zusammen passen.
Ein Update mit dem Paketmanager der installierten
TeX-Distribution hilft hier weiter.

Auch [Biber »data source not
found«](http://texwelt.de/wissen/fragen/3272/biber-data-source-not-found)
kommt ab und zu vor. 

Weitere Beispiele für häufige Fehler beim erstmaligen Laufen von
Biber erklärt Markus Kohm auf
[KOMA-Script.de](http://komascript.de/biber).

----

Möchte man bei allgemeinen Problemen in einem Forum nach Hilfe
fragen, so sollte man grundsätzlich ein [vollständiges
Minimalbeispiel](www.texwelt.de/wissen/fragen/569) erstellen.
Auch LyX-Nutzer können ihr Dokument minimalisieren
([LyX-Minimalbeispiel](http://wiki.lyx.org/FAQ/MinimalExample)),
sollten ihr Dokument dann aber noch [zu LaTeX
exportieren](http://texwelt.de/wissen/fragen/12017/wie-exportiere-ich-lyx-dokumente-zu-latex).
Nur mit Hilfe eines Minimalbeispiels können Helfer Probleme
nachvollziehen. Wichtig ist weiterhin die Bereitstellung der
erzeugten `log`- und `blg`-Dateien des Minimalbeispiels, welche
mit Hilfe des verwendeten LaTeX-Editors geöffnet werden können. 

Gerade für die Erstellung von helferfreundlichen
Minimalbeispielen stellt `biblatex` eine Beispielbibliographie
(`biblatex-examples.bib`) bereit.  Diese wird von LaTeX gefunden,
Beispiele bleiben besonders klein und überschaubar.

Weiterer Vorteil, bei goLaTeX.de kann man das Beispiel durch
»Öffne in Online-Editor« sofort testen. Sehr praktisch, wenn man
Helfern so Arbeit ersparen kann. 

    \documentclass{article}
    \usepackage[style=authoryear,backend=biber]{biblatex}
    \addbibresource{biblatex-examples.bib}
    \begin{document}
    Zitiere Onlinequelle: \cite{ctan,markey}\par
    Zitiere Buch: \parencite{companion}\par
    Zitiere Artikel: \cite{springer}
    \printbibliography[heading=bibintoc]
    \end{document}

Möchte man aus bestimmten Gründen nicht die Beispielbibliographie
nutzen, lohnt sich die Verwendung der `filecontents`-Umgebung.
Somit ist alles in einer einzigen Datei, Helfern wird das Helfen
erleichtert. Natürlich klappt dann auch das »Öffne in
Online-Editor«-Feature sofort :-)


*Ein ganz wichtiger Punkt ist hier, das Minimalbeispiel selbst in
einem extra Ordner mit einem eindeutigen Namen (beispielsweise
mit Benutzernamen:
`kurtGolatexBibTest.tex`) zu testen.* `\jobname` ist ein internes
Makro und ist der Name der Hauptdatei (ohne Dateiendung),
entsprechend wird beim ersten latex-Aufruf eine bib-Datei des
Namens `kurtGolatexBibTest.bib` geschrieben. *Das Nutzen des
Pakets `filecontents` wird nicht empfohlen!*

    %jobname NICHT ersetzen
    \begin{filecontents}{\jobname.bib}
    @online{zeilenumbruchBibliographielinks,
    	author = {TeXwelt},
    	title = {Zeilenumbrüche in Bibliografielinks},
    	url  = {http://texwelt.de/wissen/fragen/7008/},
    	urldate = {2014-07-01}
    }
    @online{bibliographieUnterteilen,
    	author = {TeXwelt},
    	title = {Wie unterteile ich meine biblatex
    Bibliografie?},
    	url  = {http://texwelt.de/wissen/fragen/7532/},
    	urldate = {2014-07-23}
    }
    \end{filecontents}
    
    \documentclass[bibliography=totoc]{scrartcl}
    \usepackage{selinput}
    \SelectInputMappings{
    	udieresis={ü}
    }
    \usepackage[ngerman]{babel}
    \usepackage[backend=biber,
    style=numeric,
    ]{biblatex}
    \addbibresource{\jobname.bib}%jobname NICHT ersetzen
    \begin{document}
    \tableofcontents
    
    \section{Zusatzinfos}
    \citetitle{bibliographieUnterteilen}
    
    Wie kann ich Links besser
    trennen?\footcite{zeilenumbruchBibliographielinks}
    \printbibliography
    \end{document} 


*Ein ganz wichtiger Punkt ist hier, das Minimalbeispiel selbst in
einem extra Ordner mit einem eindeutigen Namen (beispielsweise
mit Benutzernamen: `kurtGolatexBibTest.tex`) zu testen.*
`\jobname` ist ein internes Makro und ist der Name des Hauptdatei
(ohne Dateiendung), entsprechend wird beim ersten latex-Aufruf
eine bib-Datei des Namens `kurtGolatexBibTest.bib` geschrieben. *Das Nutzen des
Pakets `filecontents` wird nicht empfohlen!*



Anpassen des Stils an vorhandene Vorgaben
----------------

Viele Institute und Einrichtungen stellen sehr genaue
Anforderungen an das optische Erscheinungsbild der Zitationen im
Text und des Literaturverzeichnisses. Bei Kenntnis der
biblatex-Dokumentation ist das Anpassen zwar relativ simpel, aber
trotzdem sehr zeitaufwändig. Graue Haare kann man sich meist ersparen, indem
man einen Stil sucht, der den Anforderungen am nächsten kommt und
einfach mal nett nachfragt, ob das reicht. 

Ist die strikte Umsetzung gefordert kann man das Erscheinungsbild
über LaTeX-Makros ändern. Erste Schritte und Tipps werden einem
unter [Modifizieren eines
biblatex-Stils](http://texwelt.de/blog/modifizieren-eines-biblatex-stils/)
auf den Weg gegeben. Bei Fragen zur Modifikation erhöht ein
möglichst genaues Minimalbeispiel die Chancen auf eine präzise
Antwort, ist aber leider kein Garant. Dabei ist es besonders
vorteilhaft, die Details in Einzelfragen mit jeweils kleinen
Beispielen unterzubringen. Die von `biblatex` bereitgestellte
Beispielbibliographie, sowie das Paket `citeall` liefern hier
gute Dienste. 

## Anpassen von BibTeX-Stilen

Das ältere BibTeX (die Software) arbeitet mit `bst`-Dateien. In
diesen wird das Erscheinungsbild der Bibliographie über
Funktionen einer eigens entworfenen Sprache definiert.  Viele
empfinden diese Stildateien und deren Funktionen als kryptisch.
Bei allgemeinen Fragen ist wieder die Bereitstellung eines
[Minimalbeispieles](http://www.texwelt.de/wissen/fragen/569/)
wichtig, bei nicht auf CTAN befindlichen `bst`-Dateien ist auch
ein Link beziehungsweise die Bereitstellung der Stildateien
nötig. Soll das optische Erscheinungsbild geändert werden, kann
das Programm `makebst` genutzt werden. Allerdings sollte ein
Wechsel zu `biblatex` aufgrund oben bereits erwähnter Vorteile
in Erwägung gezogen werden.


------------------------
Dieser Beitrag enthält Links welche grundlegender Bestandteil des Beitrages sind. Wünsche, Kritik oder
Verbesserungsvorschläge werden im [Support-Thread](http://www.golatex.de/viewtopic,p,63146.html#63146) gern gesehen. 



Viel Erfolg     
Johannes im Namen der GoLaTeX-Helfer


2015-03-15



[l2kurz]: http://ctan.org/pkg/lshort-german
[novice]: http://www.dickimaw-books.com/latex/novices/index.html
[stefan]: https://www.packtpub.com/hardware-and-creative/latex-beginners-guide
[herbert]: http://www.lehmanns.de/shop/mathematik-informatik/18416992-9783865414151-bibliografien-mit-latex
[jabref]: http://jabref.sourceforge.net/
[thesis]: http://www.dickimaw-books.com/latex/thesis/index.html
[numeric]: http://golatex.de/files/numeric_606.png
[citekey]: http://golatex.de/files/hinweise1_157.png
[schenk]: https://portal.dnb.de/opac.htm?method=simpleSearch&cqlMode=true&query=idn%3D973206799 "Schenk, Hans-Otto, Die Examensarbeit : ein Leitfaden für Wirtschafts- und Sozialwissenschaftler, ISBN 3-8252-2657-3"
