Come fare una build della documentazione con Sphinx.
====================================================

La traduzione cerca di restare più fedele possibile agli strumenti 
usati nell'originale. Quindi dovrebbe essere possibile fare una build 
della traduzione nelle stesse condizioni in cui è possibile farlo 
per l'originale...

...ma questo purtroppo non è vero al 100%, perché nell'originale ci 
sono due hack fastidiosi, che sono difficili da replicare: 

- l'estensione ``Doc/tools/extensions/asdl_highlight.py`` richiede di 
  importare ``Parser/asdl.py`` che si trova nella repo originale ma non 
  nella nostra (perché noi "copiamo" solo la directory ``Doc``). 
  Tra l'altro questo `è noto <https://bugs.python.org/issue41331>`_ ma 
  non mi è chiaro quando e come sarà risolto. 
  Intanto noi abbiamo risolto copiando anche tutto ``Parser`` nella 
  nostra repo, (in ``Doc/Parser``) e diciamo al nostro ``conf.py`` di 
  aggiungere quella directory alla ``sys.path``.

- l'estensione ``Doc/tools/extensions/patchlevel.py`` cerca di scoprire 
  la versione di Python parsando il contenuto di ``Include/patchlevel.h``, 
  che noi, di nuovo, non abbiamo. Questo è un hack molto strano, ma non 
  possiamo farci nulla. 
  Abbiamo risolto copiando questo file in ``Include/patchlevel.h`` e 
  patchando ``patchlevel.py`` per fargli sapere dov'è il file che cerca. 

Queste patch manuali sono sgradevoli ma necessarie. Purtroppo questo 
significa che tutto il contenuto del nostro ``Doc/Parser`` non si trova 
nella stessa posizione nell'originale e pertanto l'aggiornamento di quei 
file non può essere verificato automaticamente: ogni tanto occorre 
controllare manualmente (si tratta comunque di file del tutto accessori 
che possono essere lasciati "invecchiare" senza problemi). 

Inoltre occorre tenere presente che la nostra versione dei file 

- ``Doc/tools/extensions/patchlevel.py``, 
- ``Doc/conf.py``

è leggermente diversa dai corrispondenti nell'originale. 

*Nota bene:* perché copiamo questi file dentro ``Doc`` e non li lasciamo 
fuori, come sono nell'originale? Perché ci piacerebbe che tutto ciò che 
serve per fare una build di Sphinx restasse dentro ``Doc``... e questo 
è anche ciò che serve a ReadTheDocs, in ogni caso. 

Con queste modifiche, fare una build dovrebbe essere molto facile. 

Per scrupolo, procuratevi la versione di Python indicata in 
``Doc/runtime.txt`` (anche se una più recente dovrebbe andar bene lo 
stesso). Create un virtual environment e installateci dentro quanto 
richiesto da ``Doc/requirements.txt``. A questo punto portatevi in 
``Doc`` e create la build di Sphinx, per esempio con 
``sphinx-build -b html . ./build/html``. Adesso la build dovrebbe 
trovarsi in ``Doc/build``. 

*Nota*: è possibile usare le "scorciatoie" ``Makefile`` e ``make.bat``, 
ma questi sono in realtà script complessi che possono produrre altri 
piccoli fastidi. Per esempio, ``make html`` in Windows funziona ma si 
lamenta ("Impossibile trovare il percorso specificato.") perché non 
riesce a trovare lo script accessorio ``PCbuild/find_python.bat``. In 
futuro sarà forse necessario occuparsi anche di questi dettagli. 

Infine, la build dovrebbe segnalare ancora esattamente *cinque* warning, 
per il fatto che il testo (nella versione originale) dei documenti 

- ``Doc\library\ast.rs``
- ``Doc\library\difflib.rst``
- ``Doc\library\exceptions.rst``
- ``Doc\library\wsgiref.rst``
- ``Doc\reference\grammar.rst``

ha dei riferimenti a file che si trovano fuori da ``Doc`` e che pertanto 
non esistono nella nostra repository (altri brutti hack dell'originale). 
Quando questi file verranno tradotti, vedremo come risolvere questo 
problema nella traduzione, caso per caso. Intanto ci teniamo i warning!

A parte questi cinque warning, tutto ciò che Sphinx dovesse segnalare di 
sbagliato sarebbe un problema della versione italiana. 

Se notate dei bachi, segnalateli!

*Nota* (ancora una!): i processi di build hanno inoltre un modo tutto 
loro di cercare il file ``NEWS`` (che in realtà sono diversi file nella 
directory ``Misc/NEWS.d`` dell'originale... che noi non abbiamo!). Il 
risultato finale è che il *changelog* non è disponibile nel file 
``Doc/whatsnew/changelog.rst``. Anche questo dovrà è un caso speciale 
che dovrà essere risolto nella traduzione.
