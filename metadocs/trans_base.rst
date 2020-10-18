Guida per il traduttore. Le basi.
=================================

Benvenuti!

Questa guida spiega che cosa bisogna fare per collaborare al progetto 
in qualità di traduttori. La documentazione di Python è una raccolta 
di documenti molto grande e in costante evoluzione: mantenere la 
traduzione sincronizzata e aggiornata è piuttosto complicato, dietro 
le quinte. Tuttavia questa guida si rivolge solo a chi vuole collaborare 
alla traduzione "pura e semplice", senza preoccuparsi di tutti i 
dettagli tecnici che ci stanno dietro. 

Prima di cominciare, *grazie di cuore* per la vostra collaborazione. 
Tradurre è (naturalmente!) la parte più importante di questo progetto: 
senza il vostro tempo e il vostro lavoro, niente sarebbe possibile. Se 
poi siete interessati anche alla *manutenzione tecnica* del progetto e 
a collaborare anche alle parti più complicate, allora potete farvi 
un'idea del lavoro leggendo gli altri documenti di questa directory, a 
cominciare da ``trans_advanced.rst``. 

Che cosa deve essere tradotto.
------------------------------

La documentazione di Python, all'utente finale, appare come una raccolta 
di documenti Html consultabili a partire dall'indice 
https://www.docs.python.org. 

Tuttavia noi *non* dobbiamo tradurre direttamente i file Html, che sono 
prodotti automaticamente (grazie alla libreria Sphinx). Ci interessano 
invece i *file sorgenti* della documentazione, che sono appunto quelli 
che poi sono convertiti negli Html che tutti vedono. Questi documenti 
sono file di puro testo, scritti in un formato di *markup* chiamato 
ReStructuredText (i file hanno estensione ``.rst``). 

Per intenderci, se vogliamo tradurre la documentazione del modulo 
``datetime`` della libreria standard, non dobbiamo tradurre il file 
pubblicato all'indirizzo 
https://docs.python.org/3/library/datetime.html, 
ma il file sorgente corrispondente, che nel nostro caso si trova qui: 
https://raw.githubusercontent.com/python/cpython/master/Doc/library/datetime.rst. 

E come facciamo a sapere dove si trova esattamente il file sorgente che 
corrisponde a una pagina che vogliamo tradurre? Appunto!, questa è una 
delle cose a cui *non* dovete pensare voi... 

Che cosa serve per tradurre.
----------------------------

I file sorgenti ``.rst`` sono file di puro testo: per tradurli, non va 
bene usare un programma grafico come Word. Vi serve invece un editor 
di testo "intelligente", del tipo di quelli che usano i programmatori. 

Inoltre il vostro editor dovrebbe avere queste caratteristiche: 

- aprire e salvare i file con encoding UTF-8: quindi, se siete in 
  Windows, *non usate il Blocco Note*!
- avere un minimo di supporto per la colorazione della sintassi di 
  ReStructuredText, per aiutarvi a vedere subito i link e gli altri 
  costrutti; 
- avere un correttore ortografico italiano (e quindi, di nuovo, niente 
  Blocco Note...) perché altrimenti vi caverete gli occhi a cercare gli 
  errori di battitura. 

Se siete interessati a questo progetto e state leggendo queste righe, 
sicuramente siete anche un poco "del mestiere" e quindi forse avete 
già un vostro editor di fiducia, che usate per programmare. Potete 
verificare se va bene per questo compito. Chiaramente Idle non è adatto 
(serve solo per gli script Python); nella nostra esperienza, Visual 
Studio Code ha un ottimo supporto per ``.rst``, ma l'estensione per il 
correttore ortografico consuma molte risorse; SublimeText va benissimo, 
ed è quello che infatti usa l'amministratore di questo progetto, ma non 
è semplice da configurare e *non* è gratuito. 

Un esempio di editor: Notepad++.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Se proprio non trovate di meglio, abbiamo verificato che Notepad++ può 
servire decentemente allo scopo, almeno in Windows. Sia chiaro: 
non consigliamo Notepad++ come editor "serio" per lavorare in generale, 
ma può essere una soluzione rapida per questo progetto. 

Aggiungiamo qui alcune note sulla configurazione di Notepad++ per ciò 
che serve a noi. Per prima cosa, potete scaricare l'editor qui:
https://notepad-plus-plus.org/downloads/v7.9/. Usate tranquillamente la 
versione *portable*, se non volete installare nulla di definitivo. 

Dopo aver installato/scompattato l'eseguibile, il passaggio successivo 
è fornirlo del supporto per i file ``.rst``. Questa è una discreta 
grammatica per questo formato: 
https://raw.githubusercontent.com/steenhulthin/reStructuredText_NPP/master/reStructuredText.xml
Salvate questo file (come ``reStructuredText.xml``) e copiatelo nella 
directory ``userDefineLangs`` della vostra installazione. 

Adesso potete aprire Notepad++ e noterete che, se aprite un qualsiasi 
file ``.rst``, questo viene riconosciuto e colorato automaticamente. 
Potete modificare ``reStructuredText.xml`` per cambiare i colori 
proposti (per esempio, il testo a noi sembra decisamente troppo chiaro). 

Il passaggio successivo è il correttore ortografico: andate nel menu 
``Plugins -> Plugins admin...`` e selezionate dall'elenco il plugin 
``DSpellCheck``, quindi cliccate su ``Install``. Dopo l'installazione, 
andate nel menu ``Plugins -> DSpellCheck -> Settings...`` e alla voce 
``Library`` selezionate ``Native (Windows)``. Siccome verosimilmente il 
vostro computer è già localizzato in Italiano, vedrete che alla voce 
``Language`` viene già impostato ``Italian (Italy)``. Non vi resta che 
confermare con ``Ok``. 

Infine, potete configurare Notepad++ come preferite per i vostri gusti. 
Come minimo, è consigliabile impostare una riga di margine alla colonna 
80: si può fare in ``Settings -> Preferences... -> Editing``. Se volete 
cambiare il font, potete andare in ``Settings -> Style Configurator... 
-> Global Styles``: noi per esempio preferiamo usare Consolas in corpo 
12. 

Questo dovrebbe essere più che sufficiente per tutto il lavoro di 
traduzione dei file ``.rst`` di questo progetto. 

Come iniziare a tradurre.
-------------------------

Dopo aver configurato il vostro editor, siete pronti a iniziare! 
La prima domanda, adesso, è: che cosa posso tradurre?

Tradurre un file, tradurre una sezione.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Questo progetto di traduzione si impegna a mantenere sincronizzati i 
file tradotti con gli originali. Non vi serve conoscere i dettagli 
tecnici di tutto questo. L'unica cosa importante adesso è che, come 
conseguenza, siamo impegnati a mantenere allo stesso livello di 
sincronizzazione alcune *sezioni* della documentazione. Ci sono 
quindi due tipi di traduzione differenti: tradurre un singolo file, 
oppure tradurre una sezione intera della documentazione. 

Ovviamente la seconda cosa è molto più lunga e gravosa. 
Se ve la sentite, però, sarebbe davvero fantastico!

Tenete conto tuttavia che queste sezioni: 

- Distributing Python modules
- Extending and Embedding
- FAQ
- Language Reference
- Python Setup and Usage
- Tutorial (che è stato già tradotto!)

sono disponibili **esclusivamente** come traduzione "per sezione". Non 
è possibile tradurre un solo file di queste sezioni, ma occorre invece 
farsi carico di tradurre *tutta la sezione in una volta sola*. 

Tutte le altre sezioni (per esempio la Libreria Standard), invece, sono 
traducibili "per singolo file": potete scegliere liberamente un file in 
queste sezioni, e decidere di tradurre solo quello. 

Come fare una richiesta di collaborazione.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Scegliete un file (o una sezione intera!) che non sia già stato 
tradotto e **aprite una issue** nella nostra repository GitHub. 

Questo può essere fatto facilmente nell'interfaccia web di GitHub: 
`qui <https://docs.github.com/en/free-pro-team@latest/github/managing-your-work-on-github/creating-an-issue>`_, 
trovate le istruzioni complete, ma essenzialmente si tratta di fare clic 
su ``Issues`` e poi fare clic su ``New Issue``. 

Nel testo della *issue* scrivete il capitolo della documentazione che 
volete tradurre (o la sezione!). Dopo di che, tenete d'occhio la *issue*: 
nella risposta troverete il file ``.rst`` da tradurre. 

**Attenzione!** Non cominciate a tradurre "qualcosa", prima di aver 
ricevuto il file dall'amministratore del progetto! Il file che ricevete 
è *taggato* con uno specifico commit dell'originale, e questo consentirà 
di mantenerlo sincronizzato in futuro: di nuovo, i dettagli tecnici non 
sono importati. Ma se traducete qualsiasi altra cosa che non sia 
esattamente il contenuto di *quel file*, non c'è garanzia che il lavoro 
che state facendo sarà corretto. 

**Se non avete un account su GitHub.** Potete aprire una *issue* solo se 
avete un account. Se non lo avete, e non avete voglia di crearvene uno, 
nessun problema: scrivete una email a "ric.pol<chiocciola>libero.it". 

**Scadenze.** Nel momento in cui vi viene assegnata una traduzione, 
quel file resta bloccato e non verrà assegnato a nessun altro. Per 
evitare che le traduzioni restino in sospeso per sempre, avete 
*15 giorni* di tempo per riconsegnare il file tradotto (rispondendo nel 
thread della *issue* che avete aperto, o via email). Se avete bisogno 
di più tempo, potete naturalmente chiedere una proroga. 

Tradurre una sezione.
^^^^^^^^^^^^^^^^^^^^^

Se volete tradurre, invece di un solo documento, una intera sezione... 
beh, prima di tutto *grazie*!

La procedura è pressoché identica: fate la richiesta aprendo una *issue* 
e vi verranno forniti tutti i file di quella sezione. Naturalmente il 
tempo a disposizione sarà maggiore, in questo caso. 

Per i nuovi collaboratori, chiediamo tuttavia di cimentarsi con un file 
singolo, prima di iniziare a lavorare su una sezione intera. 

Come tradurre. 
--------------

Vi consigliamo di tradurre sovrascrivendo lo stesso file che avete 
ricevuto (fatene comunque una copia per sicurezza, prima). Questo vi 
consente di rispettare più facilmente la struttura, i blocchi di testo, 
e così via. Inoltre fa risparmiare tempo quando potete conservare le 
righe che non devono essere tradotte (come gli esempi di codice). 

Semplicemente, traducete un paragrafo alla volta, cancellando il testo 
inglese man mano che lo traducete. 

Talvolta la struttura del file ``.rst`` può confondere le idee: è meglio 
tenere anche sotto mano la versione Html della pagina che state 
traducendo, pubblicata in https://docs.python.org, per farsi un'idea 
più precisa di come i diversi elementi saranno composti nel *rendering* 
finale. 

Che cosa leggere adesso.
------------------------

Per non appesantire troppo questa guida, manteniamo altri due file 
separati in questa directory, che dovreste leggere a questo punto:

- ``style.rst`` contiene indicazioni di stile *molto importanti* sulla 
  traduzione italiana, compreso un piccolo glossario di termini comuni; 
- ``rst_notes.rst`` specifica nel dettaglio come tradurre gli elementi 
  della sintassi ReStructuredText: è importante soprattutto se non 
  avete familiarità con questo linguaggio di markup. 

La lettura di entrambi questi file è **fortemente raccomandata** per 
tutti i collaboratori: è molto importante iniziare il lavoro di 
traduzione solo dopo aver letto e capito queste indicazioni. 

Grazie ancora del vostro contributo!
