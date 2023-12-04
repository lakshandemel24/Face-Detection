# FaceDetection_Realtime
Questo è un progetto basato su Python 3 per eseguire il rilevamento veloce e accurato dei volti utilizzando il rilevamento dei volti di OpenCV su video, flussi video e webcam utilizzando un modello di rilevamento dei volti addestrato in profondità incluso nella libreria.

## Dipendenze
1. Python 3.x, OpenCV 3 or 4
2. Aprire il terminale e installare numpy, imutils e OpenCV
   * ``` pip install numpy```
   * ``` pip install imutils```
   * ``` pip install opencv-python```


## Passi di Esecuzione
1. Aprire il terminale e inserire il percorso del file nella directory desiderata e incollare il comando fornito di seguito
2. ```python detect_faces_video.py --prototxt deploy.prototxt.txt --model res10_300x300_ssd_iter_140000.caffemodel```

## Spiegazione dell'algoritmo
File di riferimento: [detection_faces_video](detect_faces_video.py)

Vediamo come ottenere un rilevamento veloce e preciso del volto con OpenCV utilizzando un modello basato su **deep learning** preaddestrato fornito con la libreria dalla versione 3.3. Andremo ad usare un deep learning framework chiamato “Caffe”.

Quando si utilizza il modulo di “deep neural network” di OpenCV con modelli Caffe-based, sono necessari due insiemi di file, che troviamo all’interno della sotto-directory "face_detector" degli sample di dnn (deep neural network) di OpenCV:

- Il file .prototxt (o file .prototxt multipli) che definisce l'architettura del modello (ovvero, gli strati stessi);
- Il file .caffemodel che contiene i pesi effettivi per gli strati del modello.

Per prima cosa importiamo i pacchetti necessari e analizziamo gli argomenti da riga di comando (linee 1-20).

Da qui carichiamo il nostro modello e creiamo un blob dalla nostra immagine (linee 23-24/39-41).

**Blob Detection**

Il metodo dnn.blobFromImage si occupa della pre-elaborazione, che include la configurazione delle dimensioni del blob e la normalizzazione. Questo metodo è il fulcro dell’algoritmo, andiamo più nel dettaglio…

Il nuovo modulo di rete neurale profonda (dnn) di OpenCV contiene la funzione “cv2.dnn.blobFromImage” che si deve utilizzare per la preelaborazione delle immagini e la loro preparazione per la classificazione tramite modelli di deep learning preaddestrati.

Per ottenere previsioni corrette da reti neurali profonde, è prima necessario pre-elaborare i dati.

```blob = cv2.dnn.blobFromImage(image, scalefactor=1.0, size, mean, swapRB=True)```

Andiamo a vedere ciascun parametro di seguito:

- image: Questa è l'immagine di input che vogliamo elaborare prima di passarla attraverso la nostra rete neurale profonda per la classificazione.
- scalefactor: Questo valore predefinito è **`1.0`** (cioè nessun ridimensionamento), ma possiamo fornire anche un altro valore.
- size: Qui forniamo la dimensione spaziale che la rete neurale convoluzionale si aspetta. Per la maggior parte delle moderne reti neurali all'avanguardia, questa è 224×224, 227×227 o 299×299.
- mean: Questi sono i valori di sottrazione della media (Mean Subtraction). Possono essere una tripla di valori medi RGB oppure possono essere un singolo valore, nel qual caso il valore fornito viene sottratto da ogni canale dell'immagine. Se si sta eseguendo la sottrazione della media, assicurarsi di fornire la tripla in ordine **`(R, G, B)`**, specialmente quando si utilizza il comportamento predefinito di swapRB=True.
    - (La sottrazione della media viene utilizzata per contrastare i cambiamenti di illuminazione nelle immagini di input nel nostro dataset. Possiamo quindi considerare la sottrazione della media come una tecnica utilizzata per assistere le nostre reti neurali convoluzionali.)
- swapRB: OpenCV assume che le immagini siano nell'ordine dei canali BGR; tuttavia, il valore di mean assume che stiamo utilizzando l'ordine RGB. Per risolvere questa discrepanza, possiamo scambiare i canali R e B nell'immagine impostando questo valore su True. Per impostazione predefinita, OpenCV esegue questo scambio dei canali per noi.

→ La funzione cv2.dnn.blobFromImage restituisce un blob, che è la nostra immagine di input dopo la sottrazione della media, la normalizzazione e lo scambio dei canali. Ma cos’è un blob? 

![7 PNG](https://github.com/lakshandemel24/Face-Detection/assets/95341218/abc00b6e-6c39-4f99-9173-e0b5efac0a5b)

Un BLOB è un gruppo di pixel connessi in un'immagine che condividono una proprietà comune (ad esempio, il valore di scala di grigi). Nell'immagine sopra, le regioni connesse scure sono blobs, e il rilevamento dei blob mira a identificare e marcare queste regioni.


Ritornando al nostro codice, andremo ad applicare la face detection, passando il blob attraverso la rete (linee 43-46)...

Da lì, cicleremo sulle rilevazioni e disegneremo delle caselle intorno ai volti rilevati (linee 49-65).

Noi applichiamo l'algoritmo in real time su una web cam. Semplicemente, grazie ai tre pacchetti aggiuntivi: VideoStream, imutils e time, precedentemente importati, potremo ottenere un rilevamento dei volti sui frame del nostro video-stream. 
