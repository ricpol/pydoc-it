Sincronizzare la traduzione con l'originale.
============================================

Non basta semplicemente tradurre i file originali: occorre anche tenere 
traccia di *quando* sono stati tradotti e aggiornare la traduzione nel 
tempo, mantenendo ciascun file in sincrono con le successive modifiche 
degli originali. 

Il modo che abbiamo per fare questo è "taggare" ciascun file della 
traduzione con un "tag di sincronizzazione" (*synctag*, per gli amici). 

Tag di sincronizzazione.
------------------------

Ogni file della documentazione ``Doc/*`` deve avere un synctag. 
Un synctag contiene il nome e la data del commit del file originale, 
al momento di essere stato tradotto. Un synctag ha la forma ::

    commit: 287b84de939 | data: 2019-05-20

e viene inserito in ogni file tradotto subito dopo il titolo inizial, 
in un riquadro dal titolo ``.. topic:: Traduzione italiana:`` che può 
inoltre contenere informazioni aggiuntive sulla traduzione (il nome del 
traduttore, note varie). 

Esiste poi una pagina accessoria, dove il significato di questo strano 
tag viene spiegato anche al lettore finale della documentazione. 

I file non ancora tradotti hanno un synctag del tipo ::

    commit: XXX | data: XXX

perché verranno sincronizzati per la prima volta al momento della 
traduzione.

Due note importanti: 

- la parte "commit" riporta lo hash breve (le prime 11 cifre esadecimali, 
  in caratteri minuscoli) del commit del corrispondente file originale, 
  *al momento di essere tradotto*; 
- la parte data riporta la *author date* (e non la *commit date*) del 
  commit: la differenza tra le due è di solito insignificante, ma la 
  *author date* dovrebbe sempre essere precedente, e questo ci serve. 
  Si noti che un normale ``git log`` riporta la *author date*. 

Per esempio, per vedere hash e data dell'ultimo commit di un file, 
basta fare::

    git log -1 --format="%h %aI" -- path/al/file

La data del commit non è essenziale, ma è comoda da leggere per l'utente 
finale, e ci semplifica la vita quando dobbiamo poi cercare le 
differenze. 

Si noti che ``format="%h"`` restituisce le *prime* 11 cifre, mentre 
nella "history" di un file su GitHub vediamo le *ultime* 7 cifre. 
Questo in effetti può confondere le idee, ma per al lettore occasionale 
basta confrontare la data. 

Sincronizzare per file o per sezione.
-------------------------------------

Le traduzioni possono essere tenute in sincrono in due modi: 

- per i file ``Doc/library/*`` della libreria standard, tra gli altri, 
  adottiamo un approccio di sincronizzazione "per file": ovvero, ogni 
  file è tradotto separatamente e indipendentemente dagli altri, e 
  quindi ogni file ha il suo synctag;
- per i file di certe sezioni più omogenee (il Tutorial, per esempio), 
  adottiamo un approccio "per sezione": ovvero, ci impegniamo a 
  mantenere tutti i file di quella sezione sempre allo stesso livello di 
  aggiornamento. Pertanto queste sezioni hanno un solo synctag, sempre 
  collocato nel file ``index.rst`` della sezione. 

Le parti che teniamo sincronizzate "per sezione" sono: 

- ``Doc/distutils/*`` (Distributing Python modules);
- ``Doc/extending/*`` (Extending and Embedding)
- ``Doc/faq/*`` (FAQ)
- ``Doc/reference/*`` (Language Reference)
- ``Doc/tutorial/*`` (Tutorial)
- ``Doc/using/*`` (Python Setup and Usage)

File ``synctags.py``.
---------------------

Nella documentazione sono presenti numerosi file accessori (immagini, 
moduli ``.py`` etc.) che non possono avere un synctag incorporato. 
Anche se questi file non devono essere tradotti, dobbiamo comunque 
mantenerli aggiornati.

Per questo teniamo un registro di questi synctag nel file 
``utils/synctags.py``. 

Questo modulo contiene un elenco dei file della documentazione, e per 
ciascuno indica se il synctag si trova all'interno del file, oppure nel 
file ``index.rst`` della sua sezione, oppure appunto nello stesso 
``synctags.py``. 

La directory ``Doc/Parser`` contiene dei file che nella repository 
originale si trovano altrove, e che non fanno parte della documentazione 
(il motivo di questa irregolarità è spiegato in ``build.rst``). Il file 
``synctags.py`` mantiene un elenco anche di questi file, con il loro synctag 
e la posizione originale nella repository di CPython. 

Come sincronizzare.
-------------------

XXX

(Aggiungere che tutto il processo deve essere replicato per ciascun branch)
