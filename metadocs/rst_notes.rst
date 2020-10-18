Traduzione dei tag ReStructuredText.
====================================

La documentazione di Python è scritta (e va tradotta) in 
ReStructuredText, che è il formato compreso da Sphinx. Potete trovare 
una buona introduzione a ReStructuredText nella 
`documentazione di Sphinx <https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html>`_. 

Tuttavia non è davvero necessario conoscere nei dettagli questo formato 
per tradurre la documentazione: basterà rispettare i markup esistenti 
senza "romperli". 

In questo documento forniamo qualche indicazione aggiuntiva e qualche 
suggerimento per la traduzione del markup: si tratta comunque di cose 
molto intuitive.

Righe vuote.
------------

In generale, ReStructuredText richiede di lasciare una riga vuota in 
molti punti strategici. Per esempio, una riga vuota separa due 
paragrafi. Dopo un titolo occorre lasciare la riga vuota. E così via. 

Non è necessario conoscere tutte le regole: semplicemente, lasciate la 
riga vuota negli stessi punti in cui la trovate nell'originale. 

Rientri. 
--------

Sono molti anche i casi in cui occorre rientrare il testo: per esempio 
le liste, o gli esempi di codice. Anche qui, seguite semplicemente 
quello che fa il testo originale.

Margine.
--------

Andate sempre a capo dopo 80 caratteri, come fa il testo inglese. 
Ricordate tuttavia di terminare la riga con uno spazio, altrimenti 
l'ultima parola verrà unita alla prima della riga successiva, nella 
renderizzazione. ::

    (...) termino la riga nel modo↵
    sbagliato...

    (...) termino la riga nel modo ↵
    giusto. 

"Doppio due punti".
-------------------

Troverete spesso un "doppio due punti" che precede gli esempi di codice 
rientrato:: 

    (...) ed ecco un esempio di codice::

        >>> print('hello')

Non è un errore, e dovete usare il "doppio due punti" anche in Italiano. 
Tuttavia bisogna sapere come si comporta questo segno: 

- se è attaccato alla parola (``codice::``) allora viene renderizzato 
  come un normale "due punti";
- se è staccato dalla parola (``codice ::``) allora *non* viene 
  renderizzato e serve solo a introdurre sintatticamente il codice
  seguente. 

Il primo caso è il più comune, ma ogni tanto troverete anche esempi del 
secondo: il senso della frase vi guiderà per capire se il "due punti" 
deve essere renderizzato oppure no. 

Backtick.
---------

Il carattere "backtick" ``(`)`` è onnipresente in ReStructuredText: 
purtroppo non è possibile inserirlo con una tastiera italiana. Ci sono 
molti modi, più o meno avventurosi, per aggiungere caratteri a una 
tastiera. 

La cosa più facile, tuttavia, è semplicemente copincollare il backtick 
dove serve: di sicuro è il modo in cui l'autore di questo testo ha 
sempre lavorato senza troppi problemi.

Titoli.
-------

I titoli sono sempre sottolineati (e talvolta anche soprallineati) in 
vario modo. La cosa importante da sapere, quando si traduce, è che la 
sottolineatura deve estendersi a *tutto* il titolo::

    This is a title.
    ================

    Questo è un titolo.
    ================        <-- sbagliato!!

    Questo è un titolo.
    ===================     <-- ok

Rispettate *esattamente* il tipo di sottolineatura che trovate 
nell'originale, per conservare la medesima formattazione. 

Link.
-----

I link in senso proprio sono rari nella documentazione: sono quelli che 
citano espressamente una URL esterna. La loro sintassi è ::

    `testo visibile <URL>`_ (con l'underscore finale!)

Per esempio::

    this is a link to a `search engine <https://www.google.com>`_.
    questo è un link a `un motore di ricerca <https://www.google.com>`_. 

Nella traduzione dovete lasciare naturalmente la URL intatta, ma siete 
liberti di tradurre il testo visibile. 

Riferimenti.
------------

I riferimenti sono numerosissimi, e hanno molti diversi formati, tutti 
con la stessa sintassi di base::

    :keyword:`<testo visibile> riferimento` (senza underscore finale)

Qui ``keyword`` specifica il tipo di riferimento (viene renderizzato in 
modo diverso a seconda dei casi); ``riferimento`` è la localizzazione 
dell'oggetto riferito; ``testo visibile`` è il testo che si legge. 

Si noti che nella maggior parte dei casi la parte "testo visibile" in 
realtà viene omessa: in questo caso verrà renderizzato il nome del 
"riferimento". 

Per esempio::

    :func:`max` è un riferimento alla funzione "max"
    :meth:`~dict.items` si riferisce al metodo "items" di un dizionario
    :exc:`ValueError` si riferisce all'eccezione "ValueError"
    :mod:`datetime` si riferisce al modulo "datetime"
    :keyword:`return` si riferisce alla parola riservata "return"

In generale non avete bisogno né di conoscere la sintassi di questi 
riferimenti, né di tradurli: lasciateli esattamente come sono. 

Riferimenti ad altre pagine.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Un caso particolare sono i riferimenti di tipo ``:ref:``, che puntano 
ad altre pagine (o particolari sezioni nelle pagine) della 
documentazione. Ecco un esempio::

    Consult the :ref:`installing-index` guide ...

Questi riferimenti vengono renderizzati visualizzando il titolo del 
capitolo o del paragrafo a cui si riferiscono: in questo caso :: 

    Consult the Installing Python Modules guide ... 

Se il titolo in questione appartiene a un documento che è già stato 
tradotto, ovviamente verrà visualizzato in Italiano; altrimenti 
resterà in Inglese. 

Il problema qui è che occorre trovare una traduzione che funziona bene 
con il titolo originale inglese, ma che funzionerà anche una volta che 
il titolo verrà tradotto. Per esempio, si potrebbe rendere così::

    Consultate la guida :ref:`installing-index` ...

ma certamente *non* così::

    Consultate la guida alla :ref:`installing-index` ...

perché questo presuppone che il titolo verrà tradotto con "Installazione 
dei moduli Python"... cosa che a priori non possiamo sapere! Se, in 
futuro, qualcuno dovesse invece tradurre "Installare i moduli Python", 
la nostra frase non avrebbe più senso, e a questo punto sarebbe 
difficile ricordarsi di modificarla. 

Nei casi più difficili, quando è difficile incastrare il riferimento 
nel flusso della frase, è possibile "mascherare" il titolo della sezione 
aggiungendo un "testo visibile" al riferimento::

    Consultate la :ref:`guida all'installazione <installing-index>` ...

Tuttavia è meglio cercare di evitare questa soluzione: è preferibile 
che il lettore veda subito il titolo del paragrafo a cui punta il link. 

Altra sintassi.
---------------

ReStructuredText prevede molta altra sintassi, di cui in genere non vi 
dovete preoccupare troppo: se vedete qualcosa che non capite, in genere 
basta *non* modificarlo!

In particolare, molti elementi seguono questo schema::

    .. qualcosa:: 

dove "qualcosa" può essere una gran varietà di parole-chiave. 
Per esempio, ::

    .. versionadded:: 3.7
    .. deprecated-removed:: 3.8 3.10
    .. note::
    .. seealso::
    .. classmethod:: datetime.today()

I primi due sono note per l'aggiunta e la rimozione di *feature*; segue 
una nota, un "vedi anche" e la documentazione di un metodo di classe. 

Se la sintassi inizia con il "doppio punto" ma non ha il "doppio due 
punti", allora è un *commento*::

    .. questo è solo un commento che non verrà renderizzato

I commenti *non* si devono tradurre!

Apostrofi "appesi".
-------------------

Chiudiamo con una raccomandazione: l'Italiano usa molto l'elisione 
e quindi l'apostrofo. 

Non lasciate mai apostrofi "agganciati" a un elemento di markup, 
perché di solito non vengono resi bene da Sphinx. ::

    this goes in the :keyword:`except` block...
    questo va nell':keyword:`except`... --> SBAGLIATO
    questo va nel blocco :keyword:`except`...  --> OK

Al limite, non preoccupatevi di lasciare le vocali consecutive::

    throws an ``Exception``...
    emette un'``Exception``... --> SBAGLIATO
    emette una ``Exception``... --> OK

Abbiamo anche notato che Sphinx ha qualche problema a renderizzare 
correttamente gli apostrofi seguiti da spazio, che in Italiano 
usiamo per certi troncamenti::

    ... l'albero ... (questo non dà problemi)
    ... un po' di ... (questo invece non funziona bene)

Fate attenzione a evitare sempre queste forme. 
