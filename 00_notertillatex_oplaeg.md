

noter til latexoplæg:

nogle gange fucker ting op, og man aner ikke hvorfor. Så er det bare med at prøve sig frem. F.eks. bibliografien der bare ikke virkede. Hvorfor ikke? Fandt ud af, at hvis 1. entry i Jabref er tom, så kan bibligrafien ikke køre. Okay. Men så skete det igen. Hmm. Ofte er latex god til at fortælle hvor fejlen er, hvilken linje i hvilken fil. Men ikke denne her gang. Så er det bare med at køre alle dokumenterne hver for sig i rapport, og så identificere dokumentet med fejlen. og så bruge \iffalse til at prøve sig frem og se hvor fejlen opstår. I mit tilfælde var det med en reference til en tekst med biblatex-keyen "gittleman2015". Her havde jeg kopieret ind fra JSTOR, og det inkluderer et abstract af teksten, der ligger i JabRef. Det er jo smart nok, men abstractet inkluderer et %-tegn, som bruges i latex til noget jeg ikke forstår, udover at hvis der står et rent %-tegn, så nægter tex at køre. Så jeg ændrede "94 % of the population" til "94 percent of the population" og så virkede det. Jeg kunne nok også have skrevet "94 \% of the population" men det andet var mere læseligt, det skal jo ikke compiles af latex.
	→ Så. Man slipper altså ikke for at deale med tumpede ting der kan gøre én vanvittig, fra tid til anden.



  Hopefully, you won't have much of a learning period to go through and
  you will reap the benefits of a nicely formatted thesis. The use of
  LaTeX in combination with \emph{Markdown} is more consistent than the
  output of a word processor, much less prone to corruption or crashing,
  and the resulting file is smaller than a Word file. While you may have
  never had problems using Word in the past, your thesis is likely going
  to be about twice as large and complex as anything you've written
  before, taxing Word's capabilities. After working with \emph{Markdown}
  and \textbf{R} together for a few weeks, we are confident this will be



brug minima moralia som tekst skabelon 




