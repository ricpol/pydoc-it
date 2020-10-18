Linee guida per la traduzione italiana.
=======================================

Formattazione.
--------------

- Rispettate rigorosamente la formattazione originale! Andate a capo, 
  lasciate righe bianche, rientrate il testo, etc. *sempre* seguendo 
  l'originale. Il vostro testo tradotto, a prima vista, dovrebbe avere 
  lo stesso aspetto dell'originale. 

- Non fate mai righe più lunghe di 80 caratteri. Ci sono pochissime 
  eccezioni legittime a questa regola: per esempio, alcune url nei link 
  sono molto lunghe, ma non è possibile spezzarle andando a capo. In 
  genere vedete subito queste eccezioni anche nell'originale. 

Resa in Italiano.
-----------------

- Usate un Italiano piano e corretto. Attenti agli errori di grammatica 
  e di sintassi!

- Non usate toni o espressioni colloquiali; siate molto prudenti con i 
  toni scherzosi, anche quando l'originale lo permetterebbe. 
  In generale, siate più conservativi dell'originale: molto spesso in 
  Inglese una espressione colloquiale ha un effetto meno evidente 
  dell'equivalente in Italiano. 

- Cercate di essere sintetici, ma privilegiate la chiarezza. Ricordate 
  che l'Italiano spesso richiede un giro di parole in più per rendere 
  lo stesso concetto. Meglio usare due parole in più che rischiare di 
  non essere chiari. 

- Evitate per quanto possibile le frasi passive, l'eccesso di 
  subordinate, troppi incisi, troppe parentesi... anche quando tutto 
  questo, occasionalmente, si trova nell'originale!

- Se possibile, mappate le frasi dell'originale uno-a-uno. Mettete il 
  punto là dove lo trovate nell'originale. Per ogni frase inglese, 
  fatene una italiana. Non sempre questo è possibile...

- Rivolgetevi al lettore in seconda persona plurale, e a voi stessi in 
  prima persona plurale. "Abbiamo parlato di (...); usate questa 
  funzione (...)", eccetera. 

Resa del contenuto.
-------------------

Esiste una sola regola: 

- non aggiungete, 
- non togliete, 
- non cambiate, adattate, interpretate 

*nulla* del testo originale. Assolutamente nulla: anche quando vi sembra 
il caso. State facendo una *traduzione*, non un *adattamento*. 

Per esempio, se trovate un link a un articolo o un tutorial esterno, 
*non* mettete un link a un articolo equivalente in Italiano; se 
l'originale ha un link a un articolo di Wikipedia in Inglese, *non* 
mettete nella traduzione il corrispondente link alla Wikipedia 
italiana. 

Non aggiungete spiegazioni, rimandi a risorse in italiano che non sono 
citate nell'originale, eccetera. 

Non scrivete cose che *voi* sapete, neanche implicitamente. Non cercate 
di dimostrare la vostra bravura o di rendere un servizio migliore al 
lettore italiano. Tutto ciò che potreste dire in più o diversamente, 
magari su argomenti di cui siete esperti e appassionati, è fantastico 
e dovete assolutamente pubblicarlo prima o poi: solo, non può essere 
questo il luogo per farlo. (Sorry.)

Se davvero sentite la necessità di chiarire qualcosa per il pubblico 
italiano, mettete una nota a piè di pagina (marcatela come *NdT*). Ma 
devono essere circostanze del tutto eccezionali, per esempio per 
spiegare un gioco di parole intraducibile.

Traduzione del codice.
----------------------

Gli esempi di codice *non si traducono*, in generale. Lasciate sempre in 
Inglese i nomi delle variabili, funzioni, classi e così via. 

Dovreste tradurre solo

- i commenti, 
- le docstring, 
- eventualmente le stringhe di testo, ma *solo* se questo migliora la 
  comprensione dei concetti spiegati in quel momento; se invece le 
  stringhe sono solo degli esempi (magari "di colore"), non traducetele.

Glossario di termini.
=====================

Come regola generale, i termini inglesi tecnici non vanno tradotti, a 
meno che ovviamente esista una traduzione già consolidata ("dizionario", 
"classe", "tupla"...). Ricordiamo che i nomi inglesi sono *invariabili* 
quando sono inseriti in un testo italiano: "1 file, 10 file" (e non 
"10 files"), etc. 

Seguono delle note su alcuni termini specifici.

- **base class**: *classe-madre* (meglio col trattino), 
  mai *classe base*. 

- **bytes** (come tipo di dati): sempre *bytes* lasciato al plurale. 
  Notare però che *bytes* (come quantità) si mette al singolare. Questo 
  talvolta genera confusione: "scrivo 10 byte in una stringa di bytes". 

- **directory**: sempre *directory* mai *direttorio* o *direttrice* 
  (ovviamente!). 

- **exception**: sempre *eccezione*, mai lasciarsi scappare *errore*. 
  Talvolta "errore" è colloquiale, ma può generare confusione. 

- **keyword** (riferito a "for", "if" etc.): *parola riservata*, in 
  senso tecnico. Può andar bene anche *istruzione* (cfr. *statement*). 

- **list comprehension**: sempre *list comprehension*, mai *comprensione 
  di lista*. 

- **namespace**: sempre *namespace*, mai *spazio dei nomi*. 

- **queue**: sempre *queue*, mai *coda*. Si può dire per chiarezza 
  "una queue (o *coda*)..." la prima volta: poi, usare sempre *queue*.

- **scope** (rif. alle variabili): sempre *scope*, mai *scopo*. Dire 
  "lo *scope* di una variabile". 

- **statement**: di solito va bene *istruzione*, anche se non è proprio 
  la stessa cosa... vedi anche *keyword*. 

- **stack**: sempre *stack*, mai *pila*. Si può dire per chiarezza 
  "uno stack (o *pila*)..." la prima volta: poi, usare sempre *stack*.

- **subclass**: *sotto-classe* (con il trattino). Quando è verbo 
  (*to subclass*), se non si vuole/può usare una perifrasi, va bene 
  anche *sotto-classare* (con il trattino). 

- **super class**: *sovra-classe* (con il trattino); non è proprio come 
  *base class* (*classe-madre*), anche se spesso sono la stessa cosa. 

- **to raise** (eccezioni): mai *sollevare*. Siccome le eccezioni sono 
  simili a segnali, si può dire "emettere un'eccezione"; talvolta 
  "innescare un'eccezione", talvolta perfino "lanciare un'eccezione". 

- **to return** (funzioni): sempre *restituire*, mai *ritornare*. 
  "La funzione restituisce un valore". Tuttavia "il valore *di ritorno* 
  della funzione" è ovviamente ammesso. 

- **virtual environment**: sempre *virtual environment*, mai 
  *ambiente virtuale*. 
