\documentclass{article}
\usepackage{graphicx} % Required for inserting images
\usepackage{amsmath}
\usepackage{hyperref}
\usepackage{parskip} % für Absätze
\usepackage{amsfonts} % Für Zahlenmengen
\usepackage{fancyhdr} % Paket für Kopf- und Fußzeilen
\pagestyle{fancy} % Aktiviert fancyhdr 
\usepackage[utf8]{inputenc} 
\usepackage[ngerman]{babel} 
\usepackage[T1]{fontenc}   
\usepackage{url} % benötigt für URL in Literaturverzeichnis

\title{Abgabe 1 für Computergestützte Methoden}
\author{Gruppe 72\\\\Moritz Kerker, 4241512\\Rocco Dietrichs, 4371653\\Lennard Deppe, 4363656}
\date{Abgabedatum: 2.12.2024}

\begin{document}

% Title, Autor und Datum erzeugen
\maketitle
\tableofcontents


\newpage

\fancyhead{} %entfernt Text der Kopfzeile
\renewcommand{\headrulewidth}{0pt} %entfernt Linie der Kopfzeile

\section{Der zentrale Grenzwertsatz}
Der zentrale Grenzwertsatz (ZGS) ist ein fundamentales Resultat der Wahrscheinlichkeitstheorie, das die Verteilung von Summen unabhängiger, identisch verteilter (\textit{i.i.d.}) Zufallsvariablen (ZV) beschreibt. Er besagt, dass unter bestimmten Voraussetzungen die Summe einer großen Anzahl solcher ZV \mbox{annähernd} normalverteilt ist, unabhängig von der Verteilung der einzelnen ZV. Dies ist besonders nützlich, da die Normalverteilung gut untersucht und mathematisch
handhabbar ist.

\subsection{Aussage}
Sei $X_1,X_2,...,X_n$ eine Folge von \textit{i.i.d.} ZV mit dem Erwartungswert $\mu = \mathbb{E}(X_i)$ und der Varianz $\sigma^2 = Var(X_i)$, wobei $0 < \sigma^2 < \infty $ gelte. Dann konvergiert die standardisierte Summe $Z_n$ dieser ZV für $n \to \infty$ in Verteilung gegen eine Standardnormalverteilung:\footnote{1Der zentrale Grenzwertsatz hat verschiedene Verallgemeinerungen. Eine davon ist der \textbf{Lindeberg-Feller-Zentrale-Grenzwertsatz}\cite[Seite 328]{AchimKlenke},der schwächere Bedingungen an die Unabhängigkeit und die identische Verteilung der ZV stellt.}
\begin{equation}
    \label{Formel1}
    \ Z_n = \frac{\sum_{i=1}^n X_1 - n\mu}{\sigma \sqrt{n}} \overset{d}{\to} \mathcal{N}(0, 1).
\end{equation}
Das bedeutet, dass für große \textit{n} die Summe der ZV näherungsweise normalverteilt ist mit Erwartungswert $n\mu$ und Varianz $n\sigma^2$:
\begin{equation}
    \label{Formel2}
    \sum_{i=1}^n X_i \sim \mathcal{N}(n\mu, n\sigma^2).
\end{equation}

\subsection{Erklärung der Standardisierung}
Um die Summe der ZV in eine Standardnormalverteilung zu transformieren, subtrahiert man den Erwartungswert $n\mu$ und teilt durch die Standardabweichung $\sigma \sqrt{n}.$ Dies führt zu der obigen Formel \eqref{Formel1}. Die Darstellung \eqref{Formel2} ist für $n \to \infty$ nicht wohldefiniert.

\subsection{Anwendungen}
Der ZGS wird in vielen Bereichen der Statistik und der Wahrscheinlichkeitstheorie angewendet. Typische Beispiele sind:
\begin{itemize}
    \item Hypothesentests
    \item Konfidenzintervalle
\end{itemize}

\newpage

\section{Bearbeitung zur Aufgabe 1}
\subsection{(Berechnung der höchsten mittleren Temperatur)}
Hier haben wir Excel verwendet, um die höchste mittlere Temperatur zur ermitteln. Dazu haben wir folgenden Code verwendet:
\begin{figure}[ht] % oder t, falls Grafiken immer oben ("top") erscheinen sollen
    \centering
    % benötigt \usepackage{graphicx} in der Präambel
    \includegraphics[width = \textwidth]{Excel1.png}
    % mit in \renewcommand{\figurename}{Abbildung} zu "Abbildung" umbenennen
    \caption{Die Tabellenkalkulation}
    \label{fig:Excel}
\end{figure}
Der verwendete Befehl lautet: MAX(J25877:J26241). Dieser liefert uns den größten Wert der Spalte J zwischen den Zeilen 25877 bis 26241. Dieser ist genau der Bereich unserer Gruppe. Der gelieferte Wert lautet 83. Dies muss noch noch in Grad Celsius umgerechnet werden. Dies Erfolgt durch folgende Formel: $(83 - 32) * 5/9=28,3333333$. Somit beträgt die höchste mittlere Temperatur 28,33 Grad Celsius.

\subsection{(Datenbank-Schema entwerfen)}
Da in der Vorgegebenen Datei, die Daten bereits in der 1. Normalform vorliegen, müssen diese nur noch in die 2. Normalform gebracht werden. Um von der 1. Normalform in die 2. Normalform zu gelangen, müssen sinnvoll und passende Attribute zusammen in eine Gruppe gefasst werden und letztendlich über passende Keys miteinander verknüpft werden. Dazu haben wir folgende 4 Gruppen Erzeugt: Station, Zeitangaben, Wetterdaten und verleih. 
\begin{figure}[p] % oder t, falls Grafiken immer oben ("top") erscheinen sollen
    \centering
    % benötigt \usepackage{graphicx} in der Präambel
    \includegraphics[width = \textwidth]{Normalform2.png}
    % mit in \renewcommand{\figurename}{Abbildung} zu "Abbildung" umbenennen
    \caption{2. Normalform}
    \label{fig:TabelleErzeugen}
\end{figure}
\newpage
\subsection{(Umsetzung des Schemas in SQL)}
Da die vorgegebenen Daten schon in der 1. Normalform vorliegen, müssen diese nur in eine Tabelle eingefügt werden. Dazu haben wir zuerst eine Tabelle mit dem Namen Normalformeins erstellt, in der wir alle Attribute definiert haben.

\begin{figure}[ht] % oder t, falls Grafiken immer oben ("top") erscheinen sollen
    \centering
    % benötigt \usepackage{graphicx} in der Präambel
    \includegraphics[width = \textwidth]{TabelleErzeugen.png}
    % mit in \renewcommand{\figurename}{Abbildung} zu "Abbildung" umbenennen
    \caption{Tabelle erzeugen}
    \label{fig:TabelleErzeugen}
\end{figure}

Ist die Tabelle erstellt, können die Daten aus der csv Datei hineingeladen werden. Dies erfolgt über folgende Befehle:

\begin{figure}[ht] % oder t, falls Grafiken immer oben ("top") erscheinen sollen
    \centering
    % benötigt \usepackage{graphicx} in der Präambel
    \includegraphics[width = \textwidth]{ImportDaten.png}
    % mit in \renewcommand{\figurename}{Abbildung} zu "Abbildung" umbenennen
    \caption{Daten importieren}
    \label{fig:TabelleErzeugen}
\end{figure}

\newpage
\subsection{(Formulierung einer SQL-Abfrage)}

\begin{figure}[ht] % oder t, falls Grafiken immer oben ("top") erscheinen sollen
    \centering
    % benötigt \usepackage{graphicx} in der Präambel
    \includegraphics[width = \textwidth]{SQL-Abfrage.png}
    % mit in \renewcommand{\figurename}{Abbildung} zu "Abbildung" umbenennen
    \caption{SQL-Abfrage}
    \label{fig:SQL-Abfrage}
\end{figure}

Dies ist unsere Abfrage in SQL. In der ersten Zeile wird unser Datensatz ausgewählt, welchen wir betrachten wollen. Dies geschieht über SELECT. Der Max-Befehl liefert uns den höchsten Wert, des Attributs average-temperature. Die Funktion CAST stellt sicher, dass unsere Daten alle den richtigen Datentyp besitzen. Ohne Diese Funktion würden wir den Wert NA erhalten, da der Computer diesen für größer als eine Zahl hält. In der zweiten Zeile wird beschrieben, aus welcher Tabelle die Daten bezogen werden sollen. In diesem Falle die Tabelle Normalformeins, in welcher alle Daten so liegen, wie in der Excel-Tabelle. WHERE schränkt es letztendlich ein, damit nur die Daten unserer Gruppe genutzt werden. Das gelieferte Ergebnis, stimmt mit dem aus Excel überein.
\begin{figure}[ht] % oder t, falls Grafiken immer oben ("top") erscheinen sollen
    \centering
    % benötigt \usepackage{graphicx} in der Präambel
    \includegraphics[width = \textwidth]{SQL-Abfrage2.png}
    % mit in \renewcommand{\figurename}{Abbildung} zu "Abbildung" umbenennen
    \caption{SQL-Abfrage mit Umrechnung in Grad Celsius}
    \label{fig:SQL-Abfrage }
\end{figure}
\\Hier wird nun in der Abfrage, direkt mit dem Wert, die Temperatur in Grad Celsius umgerechnet.
\section{Der Github Link zu unserem Projekt}
https://github.com/LennardDeppe/Abgabe-1.git
\newpage


\bibliographystyle{plain}
\bibliography{Literatur}
\end{document}
