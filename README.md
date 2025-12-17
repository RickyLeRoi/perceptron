Previsione Superenalotto con un Percettrone
===========================================

Questo progetto implementa un **Percettrone**, il modello più semplice di rete neurale artificiale, per analizzare lo storico delle estrazioni del Superenalotto.

**Disclaimer importante:** Le estrazioni della lotteria sono eventi progettati per essere casuali e imprevedibili. Questo progetto è un esercizio **puramente didattico** finalizzato a comprendere i fondamenti del machine learning, i meccanismi di un classificatore binario e i suoi limiti. **Non deve essere utilizzato per scopi di gioco d'azzardo**, in quanto le "previsioni" generate non hanno alcuna validità statistica per predire estrazioni future.

Che cos'è un Percettrone?
-------------------------

Il Percettrone è un algoritmo di apprendimento supervisionato introdotto nel 1957 dallo psicologo Frank Rosenblatt. Può essere considerato un "neurone artificiale" e funge da **classificatore lineare binario**.

In sintesi:

*   **Obiettivo**: Imparare a separare dati in due categorie distinte (es. 0 o 1).
    
*   **Funzionamento**: Calcola una somma pesata degli input, aggiunge un valore di _bias_ e applica una _funzione di attivazione_ per produrre l'output finale.
    
*   **Formula**: Output = FunzioneDiAttivazione( (Σ (pesi \* input)) + bias )
    
*   **Limite principale**: Può risolvere solo problemi **linearmente separabili**, ovvero problemi in cui le due classi di dati possono essere divise da una singola linea retta.
    

⚙️ Funzionamento del Codice
---------------------------

Data la natura binaria del Percettrone, questo script non può prevedere una combinazione completa di 6 numeri. Invece, riformula il problema in un compito di classificazione binaria.

### 1\. Caricamento e Pre-elaborazione dei Dati

*   Lo script legge lo storico delle estrazioni da un file estrz.csv.
    
*   I dati vengono trasformati per adattarsi al modello. Ad esempio, il problema potrebbe essere semplificato in:
    
    *   **Previsione di un singolo numero**: Il modello viene addestrato per prevedere se un numero specifico (es. il 50) apparirà o meno nella prossima estrazione (1 se presente, 0 se assente).
        
    *   **Classificazione di una proprietà**: Il modello impara a classificare un'estrazione in base a una caratteristica binaria (es. "la somma dei numeri estratti sarà pari o dispari?").
        

### 2\. Addestramento del Modello

L'apprendimento avviene attraverso un processo iterativo:

1.  **Inizializzazione**: I _pesi_ e il _bias_ del percettrone vengono inizializzati con valori piccoli (casuali o nulli).
    
2.  **Iterazione (Epoche)**: Il modello cicla attraverso i dati storici più volte. Per ogni estrazione passata:
    
    1.  **Calcolo della Previsione**: Il percettrone calcola un output (0 o 1) usando i pesi correnti.
        
    2.  **Calcolo dell'Errore**: L'output viene confrontato con il risultato reale di quell'estrazione.
        
    3.  **Aggiornamento dei Pesi**: Se la previsione è errata, i pesi e il bias vengono leggermente corretti per ridurre l'errore futuro. La dimensione di questa correzione è controllata dal _learning rate_.
        
3.  **Convergenza**: Il processo si ripete finché il modello non impara a classificare correttamente i dati di addestramento (_early\_stopping_) o raggiunge il numero massimo di epoche.
    

### 3\. "Previsione"

Una volta addestrato, il percettrone può essere usato per classificare nuovi dati. L'output sarà sempre un valore binario (0 o 1) che risponde alla domanda specifica per cui è stato addestrato (es. "il numero X sarà presente?"). **Non genererà una combinazione di numeri.**

### 🚀 Come Eseguire il Notebook

Questo progetto è sviluppato all'interno di un **Jupyter Notebook (****.ipynb****)**. Per eseguirlo, non si utilizza un comando diretto da terminale come per un normale script Python, ma si interagisce con l'ambiente Jupyter.

`   pip install pandas numpy scikit-learn tensorflow   `

`   jupyter lab   `
oppure
`   jupyter notebook   `

#### Ambiente Jupyter

1.  **Naviga al file**: Si aprirà una scheda nel tuo browser. Usa l'interfaccia per navigare fino alla cartella del progetto e apri il file .ipynb.
    
2.  **Esegui le celle**: Puoi eseguire le celle di codice una per una. Seleziona una cella e premi Shift + Enter per eseguirla. In alternativa, puoi usare i pulsanti nell'interfaccia o le opzioni nel menu "Run" (es. "Run All Cells") per eseguire l'intero notebook in una volta sola.
