
HUSK!! HVIS DER ER EN TOM REFERENCE I JABREF SÅ KAN BIBLATEX IKKE KØRES *OVERHOVEDET*!! 

#Aligning Images 
By default, images align according to their "reference point," which is never what you want it to be. Put a minipage around an image to make it align properly (according to its center):
  \usepackage{graphicx}
  \begin{minipage}{2in}
    \includegraphics[width=2in,angle=-90]{foo}
  \end{minipage}

#Side-by-side tables 
Normally a tablular environment stretches the entire width of the text area (whether it looks like it should or not!). You can restrict the width with a minipage. This allows you to put two tables side-by-side:
  \begin{minipage}{2in}
    \begin{tabular}{c}
      Table1
    \end{tabular}
  \end{minipage}
  \begin{minipage}{2in}
    \begin{tabular}{c}
      Table2
    \end{tabular}
  \end{minipage}



Issue med at søge efter referencer
https://github.com/SublimeText/LaTeXTools/issues/299
You may use the command \iffalse \bibliography{bibfile.bib} \fi in your document.

I think the real issue is that you have not properly included the %! TEX-root directive as you are using a make file rather than the build tool from LatexTools


# sådan her kan man lave en ny (kortere) kommando som standin for en længere kommando:

\newcommand{\R}{\mathbb{R}}


#

Udelad hele afsnit af en tex-fil uden at skulle bruge % til det hele:

\iffalse

I don't want this to happen

\fi

du kan ændre det ved at skrive \iftrue i stedet for  \iffalse

# snippets i sublime

citation = tci
citation(tmp) = tci1, tci2 etc
citation hele bog = tccci
quotation = tqi 
nummerated list = tni
description list = tdi 
chapter = tcci
section = tsi
subsection= tssi
footnote = tfi
figure = tffi
figure2 = tfffi
table = tti
afsnit ref = tri
label = tli

# latex tools shortcuts
ctrl-l,ctrl-e gives you \emph{blah}, and the cursor moves to the end of the command.
ctrl-l,ctrl-b gives you \textbf{blah}
ctrl-l,ctrl-u gives you \underline{blah}
ctrl-l,ctrl-t gives you \texttt{blah}



# ting der skal fikses

at opdele efter typer af referencer (links, bøger, artikler etc)

opdele en større opgave eller bog i chapters

at lave forside som den bør være (med dato etc), her inklusiv at efter forside følger en blank side, samt korrekt nummerering (lige nu er den lidt sær)

at få ordentlig hyphernation

at få skift frem og tilbage mellem altex og sublime til at virke - CHECK

er der brug for det der kæmpe afsnit i preamble omkring floaters? er {float}-pakken ikke tilstrækkelig? Tjek når du står i en situation hvor du kan vurdere det.

hvorfor printer den ikke sidetal på 2. del af figurlisten?


# Latex koder

# lav ny kommando, insert den i preamblet, så kan du erstatte et tal med noget andet.

\newcommand{\newCommandName}{text to insert}


## citationer

\parencite - producerer (Jensen 2008, s. 32)
\textcite{Jensen2008} - producerer Jensen(2008)
\cite - sært format, forstår ikke helt hvorfor den er standard
\citetitle
\citeauthor
\citeyear
\nocite
\nocite{knuth:ct} %ved ikke helt hvad : gør i mellem text 
\citename
\citelist
\citefield




# paragraph stuff
\\ start a new paragraph.
\\* start a new line but not a new paragraph.
\- OK to hyphenate a word here.
\cleardoublepage flush all material and start a new page, start new odd numbered page.
\clearpage plush all material and start a new page.
\hyphenation enter a sequence pf exceptional hyphenations.
\linebreak allow to break the line here.
\newline request a new line.
\newpage request a new page.
\nolinebreak no line break should happen here.
\nopagebreak no page break should happen here.
\pagebreak encourage page break.
\smallskip
\medskip
\bigskip
\vspace{\baselineskip} For a fixed/hard, single blank line (roughly the same as \bigskip).


## emph, bold, underline, subscript, superscript etc

\textbf{greatest}



# urls
\url{<my_url>}

It will show the URL using a mono-spaced font and, if you click on it, your browser will be opened pointing at it.

\href[edit]
Usage:

\href{<my_url>}{<description>}



# lists

\begin{itemize}
  \item The first item
  \item The second item
  \item The third etc \ldots
\end{itemize}

\begin{enumerate}
  \item The first item
  \item The second item
  \item The third etc \ldots
\end{enumerate}



\begin{description}
  \item[First] The first item
  \item[Second] The second item
  \item[Third] The third etc \ldots
\end{description}



# symboler / tegn 

# indsæt 1/2
\usepackage{units}
\nicefrac{1}{2}



## koder der hører til i preamble og report:


%\setcounter{page}{1} % kan bruges til at resætte diverse ting der tæller i latex



## at få latex til at virke på ubuntu

http://tex.stackexchange.com/questions/1092/how-to-install-vanilla-texlive-on-debian-or-ubuntu


## ting der kan gøre




############ instruktioner til pakker ##########


# comment - sectioner ##

Another option is the comment package, which, like verbatim provides a comment environment, but offers the option to define arbitrary "throw away" environments that can selectively be enabled or disabled:

\documentclass{article}
\usepackage{comment}

% uncomment to include stuff in standard comment-environment
%\includecomment{comment}

% define a mysection env which content is excluded
\excludecomment{mysection}

\begin{document}
    This text will be displayed
\begin{comment}
    This text will only be displayed, if \includecomment{comment} was given
\end{comment}
\begin{mysection}
    This text will only be displayed, if \includecomemnt{mysection} was given
\end{mysection}
\end{document}
Additionally, the package provides some simple hooks into the defined environments. Instead of \includecomment{mysection} one could also use \specialcomment{mysection}{<before code>}{<after code>} to enable some comment section:

% typeset stuff in mycomment with gray text
\specialcomment{mysection}{\begingroup\color{gray}}{\endgroup}

### 	
You can use \iffalse:

\iffalse
One morning, as Gregor Samsa was waking up from anxious dreams, he discovered
that in his bed he had been changed into a monstrous verminous bug. He lay on
his armour-hard back and saw, as he lifted his head up a little, his brown,
arched abdomen divided up into rigid bow-like sections.
\fi
Of course, this has to align with other syntactical TeX structures in you document whereas you can use % much more freely. The good news is that you can introduce your own switch to make this optional:

\newif\ifdraft
\drafttrue % or \draftfalse

\ifdraft
<only shown in draft mode>
\else 
<only shown in non-draft mode>
\fi
The \else part is optional and you could use \ifdraft ... \fi if you don't need it.







