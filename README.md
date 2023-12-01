# Face-Detection
Modelli e principi della percezione

Presentazione: https://prezi.com/view/vsemGid4BFIrgBFDwykL/

# Rilevamento del volto
Il nostro cervello, con l’evolvere umano, si è abituato a vedere certe scene. Siamo abituati a vedere i visi e senza volerlo, l’umano ha capito quali sono i punti di interesse che permettono di distinguere una persona da un’altra. Ormai sono noti nella visione artificiale tutti i metodi di riconoscimento e questi sono:
- i bordi degli occhi: sia interni che esterni
- bordi bocca
- punto centrale naso
- bordi a lato sugli zigomi

I primi studi dei movimenti saccadici si fermano sui primi 3. Questo è uno studio psico-percettivo che fecero mostrando a degli individui oggetti di tipo diverso andando a vedere dove i movimenti saccadici si fermavano maggiormente (bocca, naso e occhi). Per il resto l'occhio si ferma nelle zone a più alto contrasto perchè a noi piace il contrasto.

La **face detection** negli algoritmi di visione artificiale è un processo ispirato alla biologia umana, ma implementato in modo completamente diverso.
Il rilevamento del volto viene spesso descritto come la prima delle quattro fasi del “Riconoscimento dei volti”, che sono:  
- face detection: localizzare uno o più volti nell'immagine e contrassegnarli con un riquadro delimitatore
- face alignment: normalizzare il volto in modo da renderlo coerente con il database, come la geometria e la fotometria
- feature extraction: estrarre le caratteristiche dal volto che possono essere utilizzate per il compito di riconoscimento
- face recognition: effettuare il confronto del volto con uno o più volti conosciuti in un database preparato

La **face recognition** è una tecnologia che consente di identificare e tracciare i volti umani in un'immagine o in un video. Questa tecnologia può essere utilizzata in vari contesti, come la sicurezza, la fotografia, l'analisi delle emozioni e molto altro.
Uno dei principali approcci per il **rilevamento del volto** è l'utilizzo di **algoritmi di apprendimento automatico**, come le **reti neurali convoluzionali**. Questi algoritmi sono in grado di individuare i tratti distintivi del volto umano, come gli occhi, il naso e la bocca, e di determinarne la posizione e l'orientamento. Essi utilizzano metodi matematici e modelli di machine learning per identificare e localizzare i volti nelle immagini. Questo approccio è stato particolarmente efficace grazie all'avanzamento delle reti neurali convoluzionali (CNN) e dei modelli di object detection. Alcuni punti chiave sull'argomento:

1. **Architetture di Reti Neurali:** 

Le reti neurali utilizzate per la face detection sono spesso basate su architetture di object detection, che sono progettate per individuare e localizzare oggetti in un'immagine. 

2. **Dataset di Addestramento:** 

L'addestramento di queste reti richiede un ampio dataset contenente immagini con volti annotati, che indicano la posizione esatta dei volti nell'immagine. 

**WIDER FACE** è un dataset ampio e popolare utilizzato per l'addestramento e la valutazione di modelli di face detection. È noto per la sua dimensione considerevole, la varietà di scenari e la presenza di un gran numero di immagini con volti annotati. Ecco alcune informazioni chiave 

- **Dimensioni del Dataset:** è uno dei dataset più grandi per la face detection, con oltre 32.000 immagini etichettate e più di 393.000 volti umani. Vi sono immagini acquisite in diversi scenari reali, coprendo una vasta gamma di condizioni di illuminazione, pose, espressioni facciali, sfondi e occlusioni.
- **Annotazioni:** Le immagini sono annotate con ***bounding box*** (rettangoli) che delimitano i volti presenti nell'immagine. Le annotazioni forniscono informazioni sulla posizione e le dimensioni dei volti, consentendo l'addestramento e la valutazione di modelli di face detection.
- **Scenari e Variazioni:** Le immagini coprono una vasta gamma di scenari, inclusi ritratti singoli, gruppi di persone, immagini di strada, immagini da telecamere di sorveglianza, nonché situazioni in cui i volti sono piccoli e potenzialmente difficili da individuare. Le variazioni nelle condizioni ambientali e nelle caratteristiche facciali rendono il dataset un banco di prova completo per valutare la robustezza dei modelli di face detection.
- **Divisione del Dataset:** WIDER FACE è suddiviso in un set di addestramento (train), un set di convalida (val) e un set di test. La divisione tra set di addestramento e di convalida consente di addestrare modelli sui dati di addestramento e di valutare le prestazioni sui dati di convalida.

In sintesi, WIDER FACE è un dataset chiave che ha svolto un ruolo importante nell'avanzamento delle tecniche di face detection, fornendo un ambiente di valutazione realistico e completo per i ricercatori e gli sviluppatori.

3. **Processo di Addestramento:** 

Le reti neurali per la face detection vengono addestrate attraverso un processo di apprendimento supervisionato. Durante l'addestramento, la rete impara a riconoscere i modelli e le caratteristiche che definiscono i volti attraverso la retropropagazione dell'errore. Vediamo come potrebbe avvenire questo processo:

1. **Pre-elaborazione dell'Immagine:** L'immagine in ingresso viene spesso sottoposta a operazioni di pre-elaborazione per migliorare la qualità e facilitare l'analisi. Queste operazioni possono includere correzioni di colore, normalizzazione luminosa e altre trasformazioni.
2. **Estrazione di Caratteristiche:** Gli algoritmi di face detection estraggono caratteristiche rilevanti dall'immagine, come bordi, linee e texture. Ciò può coinvolgere l'uso di filtri e operatori di immagine per individuare le strutture che potrebbero corrispondere a parti del viso.
3. **Modello di Machine Learning:** Vengono utilizzati i dataset di immagini facciali. Questi modelli possono essere reti neurali convoluzionali (CNN) o altri tipi di algoritmi di classificazione e regressione.
4. **Localizzazione del Volto:** Il modello di machine learning è in grado di identificare le caratteristiche rilevanti di un volto e di localizzare la posizione approssimativa del volto nell'immagine attraverso bounding box (rettangoli che delimitano il volto).
5. **Post-elaborazione:** Dopo la localizzazione iniziale, possono essere eseguite operazioni di post-elaborazione per migliorare la precisione e la coerenza dei risultati, ad esempio eliminando sovrapposizioni indesiderate o applicando correzioni geometriche.
6. **Output della Face Detection:** Il risultato finale è l'output della face detection, che fornisce le coordinate della bounding box che delimita il volto nell'immagine.

4. **Approccio di Object Detection:** 

L'object detection tratta il rilevamento di volti come un problema di individuazione di oggetti all'interno di un'immagine. I modelli dividono l'immagine in regioni proposte (region proposal) e applicano la classificazione e la regressione delle coordinate per identificare e localizzare i volti.

5. **Caratteristiche Discriminanti:** 

Le reti neurali apprendono automaticamente caratteristiche discriminanti dei volti, come contorni degli occhi, naso e bocca. L'utilizzo di layer convoluzionali consente alle reti di catturare informazioni gerarchiche, aprendo la strada a una rappresentazione profonda delle caratteristiche facciali.

6. **Sfide:** 

La face detection deve affrontare sfide come variazioni di illuminazione, occlusioni parziali del viso, diverse espressioni facciali e variazioni nelle pose. La complessità aumenta quando ci sono più volti nell'immagine o quando i volti sono in movimento.

7. **Applicazioni:**

La face detection basata su reti neurali è ampiamente utilizzata in applicazioni come il riconoscimento facciale, il controllo degli accessi, la sorveglianza, la fotografia automatica (autofocus), e nelle interfacce utente basate sulla percezione del viso.

************************************L’algoritmo di Viola & Jones************************************

Un face detector deve determinare se un'immagine di dimensioni arbitrarie contiene un volto umano e, in caso affermativo, individuarne la posizione. Un framework naturale per affrontare questo problema è quello della ***classificazione binaria***, in cui si costruisce un classificatore per minimizzare il rischio di classificazione errata. L'algoritmo deve ridurre al minimo sia i tassi di falsi negativi che quelli di falsi positivi per ottenere prestazioni accettabili. Questo compito richiede una descrizione numerica accurata di ciò che distingue i volti umani da altri oggetti. 

I due studiosi Viola e Jones nel 2001 pubblicarono un articolo che descrive un approccio di apprendimento automatico per la rilevazione visuale di oggetti, motivato principlamente dal problema della “face detection”, e in grado di elaborare immagini in modo estremamente rapido (i visi vengono rilevati in 15 frame al secondo)  e di ottenere elevate percentuali di rilevamento. Sebbene abbia una precisione inferiore rispetto a metodi più moderni come le reti neurali convoluzionali, la sua efficienza e le sue dimensioni compatte (solo circa 50.000 parametri, rispetto a milioni di parametri per tipiche CNN come DeepFace) significano che è ancora utilizzato in casi con limitate risorse computazionali.

Il lavoro fatto si distingue per tre contributi chiave. 

1. Il primo è l'introduzione di una nuova rappresentazione dell'immagine chiamata "***Immagine Integrale***",  che consente una valutazione molto veloce delle caratteristiche. 
    
    Viola e Jones utilizzano un insieme di caratteristiche che ricordano le funzioni di base di ***Haar***. 
    
    Una *Haar-feature* considera regioni rettangolari adiacenti in una posizione specifica all'interno di una finestra di rilevamento, somma le intensità dei pixel in ciascuna regione e calcola la differenza tra queste somme. Questa differenza viene utilizzata per categorizzare le sezioni di un'immagine. 
    
    - Ad esempio, con un volto umano, è un'osservazione comune che tra tutti i volti la regione degli occhi è più scura rispetto alla regione delle guance. Pertanto, una caratteristica Haar comune per il rilevamento del volto è un insieme di due rettangoli adiacenti che si trovano sopra la regione degli occhi e quella delle guance. La posizione di questi rettangoli è definita rispetto a una finestra di rilevamento che funge da *bounding box* per l'oggetto di destinazione (il volto in questo caso).
    
    Al fine di calcolare queste feature molto rapidamente a molte scale, introducono la rappresentazione dell'immagine integrale per le immagini. Le immagini integrali possono essere definite come tabelle di ricerca bidimensionali sotto forma di una matrice con le stesse dimensioni dell'immagine originale. Ogni elemento dell'immagine integrale contiene la somma di tutti i pixel situati nella regione in alto a sinistra dell'immagine originale (in relazione alla posizione dell'elemento). Ciò consente di calcolare la somma di aree rettangolari nell'immagine, in qualsiasi posizione o scala:
    
    $$
    somma = I(C) + I(A)-I(B)-I(D)
    $$
    
2. Il secondo è un algoritmo di apprendimento, basato su ***AdaBoost***, che è un algoritmo di apprendimento che mira a costruire un classificatore forte combinando una serie di classificatori deboli.  Esso seleziona un piccolo numero di caratteristiche visive critiche da un insieme più ampio e produce *classificatori* estremamente efficienti. Al fine di garantire una classificazione veloce, il processo di apprendimento deve escludere la grande maggioranza delle caratteristiche disponibili e concentrarsi su un piccolo insieme di caratteristiche critiche. La selezione delle caratteristiche viene realizzata attraverso una semplice modifica della procedura di AdaBoost: 
    - Il classificatore debole è vincolato in modo che possa dipendere solo da una singola caratteristica. AdaBoost fornisce un algoritmo di apprendimento efficace e limiti robusti sulle prestazioni di generalizzazione.
3. Il terzo contributo è un metodo per combinare classificatori sempre più complessi in una "***cascata***", che consente di scartare rapidamente le regioni di sfondo dell'immagine mentre si impiega più tempo di calcolo sulle regioni simili a oggetti promettenti.
    
    Il concetto alla base degli approcci di focalizzazione dell'attenzione è che spesso è possibile determinare rapidamente dove in un'immagine potrebbe verificarsi un oggetto.  
    
    Le *sottofinestre* che non vengono respinte dal classificatore iniziale vengono elaborate da una sequenza di classificatori, ognuno leggermente più complesso del precedente. Se uno qualsiasi dei classificatori respinge la sottofinestra, non viene eseguito alcun ulteriore processo. La struttura del processo di rilevamento a cascata è essenzialmente quella di un albero decisionale degenere.

****************************************************Componenti del framework:**************************************************** 

Considera un'immagine

$$
I(x, y)
$$

di risoluzione fissa

$$
(M,N)
$$

Il nostro compito è prendere una decisione binaria: se sia una foto di un volto standardizzato (frontale, ben illuminato, ecc.) o meno.

Viola-Jones è essenzialmente un algoritmo di apprendimento delle caratteristiche potenziato, addestrato eseguendo un algoritmo AdaBoost modificato su classificatori di caratteristiche Haar per trovare una sequenza di classificatori

$$
f_1, f_2,... , f_k 
$$

I classificatori di caratteristiche Haar sono rudimentali, ma consentono un calcolo molto veloce, e l'AdaBoost modificato costruisce un classificatore forte da molti deboli.

Durante l'esecuzione, un'immagine data ***I*** viene testata sequenzialmente su 

$$
f_1(I), f_2(I),... , f_k(I) 
$$

Se in un punto qualsiasi

$$
f_1(I)=0
$$

l'algoritmo restituisce immediatamente "nessun volto rilevato". Se tutti i classificatori restituiscono 1, l'algoritmo restituisce "volto rilevato". Per questo motivo, il classificatore Viola-Jones è anche chiamato "classificatore a cascata Haar".

**Classificatori di Haar-feature**

Considera un percettrone

$$
f_w,_b
$$

definito da due variabili

$$
w(x,y), b
$$

Prende un'immagine

$$
I(x,y)
$$

di risoluzione fissa e restituisce:

![Untitled (1)](https://github.com/lakshandemel24/Face-Detection/assets/95341218/2112807f-9b81-456b-acde-a9fbcc8190aa)

Un classificatore di Haar-feature è un percettrone

$$
f_w,_b
$$

con un tipo molto speciale di ***w**,* che lo rende estremamente economico da calcolare. In particolare, se scriviamo la matrice

$$
w(x,y)
$$

scopriamo che assume solo tre valori possibili {+1,−1,0}, e se coloriamo la matrice di bianco su +1 nero su −1 e trasparente su 0 la matrice è in uno dei 5 possibili pattern mostrati a destra. Ogni pattern deve anche essere simmetrico rispetto alla riflessione x e y (ignorando il cambio di colore), quindi ad esempio, per la caratteristica bianco-nero orizzontale, i due rettangoli devono avere la stessa larghezza. Per la caratteristica bianco-nero-bianco verticale, i rettangoli bianchi devono avere la stessa altezza, ma non c'è restrizione sull'altezza del rettangolo nero.

![Untitled (2)](https://github.com/lakshandemel24/Face-Detection/assets/95341218/d8021ad5-b4bc-45ab-8546-355ca7037dd1)

**Ragionamento per le caratteristiche Haar**
Le caratteristiche Haar utilizzate nell'algoritmo di Viola-Jones sono un sottoinsieme delle più generali funzioni di base di Haar, che sono state utilizzate in precedenza nel campo della rilevazione di oggetti basata sull'immagine.

Sebbene rudimentali rispetto a alternative come i filtri steerable, le caratteristiche Haar sono sufficientemente complesse per corrispondere alle caratteristiche tipiche dei volti umani. Ad esempio:

- La regione degli occhi è più scura rispetto alle guance superiori.
- La regione del ponte del naso è più luminosa rispetto agli occhi.

Composizione delle proprietà che formano caratteristiche facciali adattabili:

- Posizione e dimensione: occhi, bocca, ponte del naso.
- Valore: gradienti orientati delle intensità dei pixel.

Inoltre, la progettazione delle caratteristiche Haar consente un calcolo efficiente di 

$$
f_w,_b(I)
$$

utilizzando solo un numero costante di addizioni e sottrazioni, indipendentemente dalle dimensioni delle caratteristiche rettangolari, utilizzando la tabella di area sommata.

**Apprendimento**

Raccogli un set di addestramento, con alcune immagini contenenti volti e altre non contenenti volti. Esegui un addestramento AdaBoost modificato su tutto l'insieme di classificatori di caratteristiche Haar di dimensione ***(M,N),*** fino a raggiungere un livello desiderato di precisione e richiamo. L'algoritmo AdaBoost modificato restituirebbe una sequenza di classificatori di caratteristiche Haar

$$
f_1, f_2,... , f_k 
$$

**Utilizzo**

Per utilizzare un classificatore Viola-Jones con 

$$
f_1, f_2,... , f_k 
$$

su un'immagine ******I******, calcola

$$
f_1(I), f_2(I),... , f_k(I) 
$$

sequenzialmente. Se in un punto qualsiasi

$$
f_i(I)=0
$$

l'algoritmo restituisce immediatamente "nessun volto rilevato". Se tutti i classificatori restituiscono 1, l'algoritmo restituisce "volto rilevato".

**Algoritmo di apprendimento**

La velocità con cui le caratteristiche possono essere valutate non compensa adeguatamente il loro numero. Il framework di rilevamento oggetti utilizza una variante dell'algoritmo di apprendimento AdaBoost sia per selezionare le migliori caratteristiche sia per addestrare classificatori che le utilizzano. Questo algoritmo costruisce un classificatore "forte" come combinazione lineare di classificatori deboli "semplici" pesati.

**Architettura a cascata**

- In media, solo lo 0,01% di tutte le sottofinestre sono positive (volti).
- Il tempo di calcolo è distribuito in modo equo su tutte le sottofinestre.
- Si deve impiegare la maggior parte del tempo solo su sottofinestre potenzialmente positive.
- Un semplice classificatore a 2 feature può ottenere un tasso di rilevamento quasi del 100% con un tasso di falsi positivi del 50%. Questo classificatore può agire come primo strato di una serie per filtrare la maggior parte delle finestre negative.
Il secondo strato, con 10 feature, può affrontare finestre negative "più difficili" che hanno superato il primo strato, e così via...
- Una cascata di classificatori via via più complessi ottiene risultati di rilevamento ancora migliori. I classificatori robusti sono disposti in una cascata in ordine di complessità, dove ogni classificatore successivo è addestrato solo su quegli esempi selezionati che superano i classificatori precedenti. Se in qualsiasi fase della cascata un classificatore rifiuta la sottofinestra in ispezione, non viene eseguito alcun ulteriore processo e si continua a cercare la sottofinestra successiva. La cascata assume quindi la forma di un ***albero degenere.***
- Nel caso dei volti, il primo classificatore nella cascata, chiamato operatore di attenzione, utilizza solo due feature per ottenere un tasso di falsi negativi di circa lo 0% e un tasso di falsi positivi del 40%. L'effetto di questo singolo classificatore è ridurre di circa la metà il numero di volte in cui l'intera cascata viene valutata.

Nel processo a cascata, ogni fase consiste in un classificatore robusto. Quindi tutte le feature sono raggruppate in diverse fasi, dove ogni fase ha un certo numero di feature.

Il compito di ogni fase è determinare se una data sottofinestra non è sicuramente un volto o potrebbe essere un volto. Una data sottofinestra viene immediatamente scartata come non volto se fallisce in una qualsiasi delle fasi.

Di seguito è fornito un framework semplice per l'addestramento a cascata:

- *f* = il tasso massimo accettabile di falsi positivi per strato.
- *d* = il tasso minimo accettabile di rilevamento per strato.
- *F_target* = tasso complessivo desiderato di falsi positivi.
- *P* = insieme di esempi positivi.
- *N* = insieme di esempi negativi.
```
F(0) = 1.0; D(0) = 1.0; i = 0

while F(i) > Ftarget
    increase i
    n(i) = 0; F(i)= F(i-1)
    
    while F(i) > f × F(i-1)
        increase n(i)
        use P and N to train a classifier with n(i) features using AdaBoost
        Evaluate current cascaded classifier on validation set to determine F(i) and D(i)
        decrease threshold for the ith classifier (i.e. how many weak classifiers need to accept for strong classifier to accept)
            until the current cascaded classifier has a detection rate of at least d × D(i-1) (this also affects F(i))
    N = ∅
    if F(i) > Ftarget then 
        evaluate the current cascaded detector on the set of non-face images 
        and put any false detections into the set N.
```

***L'algoritmo SIFT*** (*Scale-Invariant Feature Transform*) 

E’ un algoritmo di computer vision ampiamente utilizzato per individuare e descrivere punti di interesse distintivi in un'immagine. Creato da David Lowe, SIFT è progettato per essere robusto alle trasformazioni geometriche e alle variazioni di scala. Ecco come funziona e alcune delle sue principali applicazioni:

1. **Individuazione dei Punti Chiave (Keypoints):** SIFT individua i punti chiave attraverso l'uso di scale di immagine multiple. A diverse scale, l'algoritmo applica *filtri di Gaussiani* per individuare i punti di massima variazione di intensità, che corrispondono a caratteristiche distintive.
2. **Descrizione dei Punti Chiave:** Una volta individuati i punti chiave, SIFT calcola le cosiddette "*signature*" o "descrittori" per ciascun punto. Questi descrittori sono basati su gradienti locali di intensità e sono progettati per essere invariabili rispetto a rotazioni e scale.
3. **Corrispondenza tra Descrittori:** I descrittori dei punti chiave in due diverse immagini possono essere confrontati per trovare corrispondenze. Questo consente di associare gli stessi punti o oggetti in diverse pose o scene.
4. **Robustezza Geometrica:** SIFT è progettato per essere robusto alle trasformazioni geometriche, come rotazioni e scale diverse, rendendolo adatto a una vasta gamma di applicazioni.

Oltre al riconoscimento degli oggetti, viene applicato anche in: 

1. **Ricostruzione 3D:** Nella visione computerizzata tridimensionale, SIFT può essere utilizzato per corrispondere punti tra diverse visualizzazioni di una scena, contribuendo alla ricostruzione 3D.
2. **Rilevamento di Oggetti in Tempo Reale:** A causa della sua robustezza alle trasformazioni geometriche, SIFT può essere implementato in sistemi di visione artificiale per il rilevamento di oggetti in tempo reale.
3. **Realtà Aumentata:** SIFT trova applicazioni nella realtà aumentata, dove può essere utilizzato per riconoscere oggetti e fornire un ancoraggio virtuale in tempo reale.
4. **Analisi Medica:** In ambito medico, SIFT può essere utilizzato per l'analisi di immagini diagnostiche, aiutando nella rilevazione di strutture anatomiche o anomalie.
5. **Stitching di Immagini:** Per creare immagini panoramiche o foto ad alta risoluzione, SIFT è spesso coinvolto nel processo di stitching, allineando e unendo diverse immagini provenienti da diverse fonti o angolazioni..

E’ importante notare che SIFT, data la sua complessità computazionale, in alcuni contesti può essere sostituito da varianti più veloci e efficienti, come ORB (Oriented FAST and Rotated BRIEF).

Scrivere un pseudocodice esaustivo per l'intero algoritmo sarebbe complesso, ma a seguire forniamo uno pseudocodice semplificato che illustra la logica di base. Questa è solo una rappresentazione concettuale, e l'implementazione effettiva richiederebbe conoscenze più approfondite della teoria e della matematica alla base di SIFT.

L'implementazione reale richiederebbe l'uso di strutture dati e algoritmi specifici. La libreria OpenCV offre un'implementazione di SIFT che può essere utilizzata direttamente in molti ambienti di sviluppo. 

***OpenCV***, acronimo di Open Source Computer Vision Library, è una libreria open source specializzata nella visione artificiale e nell'elaborazione delle immagini. Essa fornisce un vasto insieme di strumenti e funzionalità che permettono di sviluppare applicazioni che coinvolgono la manipolazione delle immagini, il riconoscimento di oggetti, il tracciamento dei movimenti, il rilevamento dei volti, la calibrazione della camera, e molte altre attività legate alla visione artificiale. La sua natura open source la rende accessibile a sviluppatori in tutto il mondo.
