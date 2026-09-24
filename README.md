# Progetto-ASD test 
Progetto di Algoritmi e Strutture dei Dati di Aya Lakhouatri
# Progetto-ASD (architettura iniziale)
Progetto di Algoritmi e Strutture dei Dati di Aya Lakhouatri


## Obiettivo del Progetto
L'obiettivo del progetto è analizzare la topologia di rete per la trasmissione dei dati su internet a livello di Autonomous Systems (AS). Questo viene realizzato utilizzando statistiche reali derivate dal protocollo BGP per costruire un grafo pesato e non orientato, in cui i nodi sono gli AS e gli archi rappresentano le connessioni osservate nei cammini BGP. Il peso di ogni arco è dato dalla frequenza con cui compare nei cammini. Sul grafo verranno poi eseguiti algoritmi per il calcolo del cammino minimax ottimo.

## 1. Principali moduli software
Il sistema sarà suddiviso nei seguenti moduli principali:
*   **DatasetParser**: Modulo dedicato all'acquisizione e decodifica dei dati.
*   **ASGraph**: Modulo per la gestione del grafo AS.
*   **MinimaxSolver**: Modulo dedicato agli algoritmi di ricerca dei cammini.
*   **ExperimentAnalyzer**: Modulo per l'analisi sperimentale e la raccolta delle metriche.

## 2. Compiti assegnati a ciascun modulo
*   **DatasetParser**: Ha il compito di leggere i file testuali contenenti i dump reali dei cammini BGP ed estrapolare le sequenze di nodi.
*   **ASGraph**: Deve costruire il grafo inserendo nodi e archi non orientati, eliminando eventuali self-loop e calcolando la frequenza (peso) di ciascun arco in base ai cammini osservati. Deve inoltre identificare e isolare la componente connessa più grande qualora il grafo non risulti completamente connesso.
*   **MinimaxSolver**: Dato il grafo costruito e due nodi di input $u$ e $v$, ha il compito di trovare il costo del cammino minimax ottimo (ovvero minimizzare la massima frequenza tra gli archi attraversati). Opzionalmente, conterà tutti i cammini che presentano tale costo ottimo.
*   **ExperimentAnalyzer**: Si occuperà di calcolare e riportare le statistiche richieste, quali numero di nodi e archi, distribuzione delle frequenze, costo ottimo minimax, numero di cammini ottimi e tempi di esecuzione.

## 3. Strutture dati fondamentali
In questa prima fase concettuale, le entità principali del sistema sono:
*   **Grafo pesato e non orientato**: Struttura centrale per rappresentare la topologia della rete degli Autonomous Systems[cite: 1].
*   **Pesi degli archi**: Valori associati alle connessioni, definiti dalla funzione $w(u,v) = f(u,v)$ che rappresenta la frequenza di comparizione dell'arco nei cammini BGP letti in input.

## 4. Principali interazioni tra moduli
*   Il **DatasetParser** elabora i dati grezzi e fornisce sequenze ordinate di nodi (cammini BGP) al modulo **ASGraph**.
*   Il modulo **ASGraph** utilizza queste sequenze per popolare la propria struttura dati fondamentale, aggiornando dinamicamente le frequenze (pesi) degli archi.
*   Una volta completata la fase di costruzione, la struttura del grafo diventa interrogabile dal **MinimaxSolver**, che la esplora per calcolare i costi dei cammini minimax ottimi tra coppie di nodi specificate.
*   L'**ExperimentAnalyzer** interagisce con **ASGraph** e **MinimaxSolver** per estrarre le informazioni strutturali (nodi, archi, frequenze) e misurare i tempi di esecuzione degli algoritmi.