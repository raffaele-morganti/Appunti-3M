# Esercizi proposti

## Base ★☆☆

### Statistiche su un vettore

Scrivi un programma che legga `N` numeri interi (con `#define N 8`) in un vettore e calcoli, usando funzioni separate: somma, media, minimo e massimo. Stampa tutti i risultati.

> [!NOTE]
> **Approfondimento**
> 
> aggiungi una funzione `conta_maggiori(int arr[], int n, int soglia)` che conti quanti elementi sono strettamente maggiori di un valore `soglia` letto da tastiera. Come cambieresti il codice se volessi contare anche quelli minori e quelli uguali con una sola scansione del vettore?

### Inversione di un vettore

Scrivi una funzione `inverti(int arr[], int n)` che inverta il vettore *sul posto* (senza creare un secondo array). Stampalo prima e dopo l'inversione.

*(Suggerimento: scambia il primo elemento con l'ultimo, il secondo con il penultimo, e così via. Quanti scambi servono?)*

## Intermedio ★★☆

### Occorrenze

Scrivi una funzione `conta_occorrenze(int arr[], int n, int target)` che conti quante volte `target` compare nel vettore. Poi scrivi `rimuovi_duplicati`: stampa ogni elemento una sola volta, anche se compare più volte.

> [!NOTE]
> **Approfondimento**
> 
> `rimuovi_duplicati` con un solo vettore richiede $O(n^2)$ confronti. Riesci a capire perché? Se il vettore fosse già **ordinato**, come cambierebbe l'approccio e perché sarebbe più efficiente?

### Rotazione

Scrivi una funzione `ruota_sinistra(int arr[], int n, int k)` che ruoti il vettore di `k` posizioni verso sinistra. Ad esempio, `{1, 2, 3, 4, 5}` ruotato di 2 diventa `{3, 4, 5, 1, 2}`.

> [!NOTE]
> **Approfondimento**
> 
> cosa succede se `k >= n`? Come gestisci il caso? *(Suggerimento: `k % n`.)*. Prova a trovarlo e implementarlo.

## Avanzato ★★★

### Calcolo di medie statistiche

Scrivi un programma che legga da tastiera N numeri interi positivi (con `#define N 5`) e li salvi in un vettore. Se l'utente inserisce un valore minore o uguale a zero, il programma deve scartarlo e richiederlo.

Il programma deve calcolare e stampare tre diverse tipologie di media utilizzando funzioni separate: 

- Media Aritmetica ($M_A$): La somma dei valori divisa per il numero di elementi.
$$M_A = \frac{1}{N} \sum_{i=0}^{N-1} x_i$$

- Media Geometrica ($M_G$): La radice $N$-esima del prodotto degli elementi. 
$$M_G = \sqrt[N]{\prod_{i=0}^{N-1} x_i} = \left( \prod_{i=0}^{N-1} x_i \right)^{\frac{1}{N}}$$
*(Suggerimento: per il calcolo della radice $N$-esima in C, puoi usare la funzione `pow(base, 1.0/N)` inclusa nella libreria `<math.h>`)*

- Media Armonica ($M_H$): Il reciproco della media aritmetica dei reciproci dei valori. 
$$M_H = \frac{N}{\sum_{i=0}^{N-1} \frac{1}{x_i}}$$

### Istogramma delle frequenze

Leggi un vettore di `N` interi compresi tra `0` e `MAX` (definisci entrambe le costanti). Costruisci un secondo vettore `frequenze` dove `frequenze[v]` conta quante volte il valore `v` compare nel primo vettore. Stampa l'istogramma orizzontale dei valori da 0 a MAX, mostrando la frequenza di ciascuno come riga di asterischi.

### Trova la coppia

Dato un vettore di `n` interi e un valore target `T`, trova due elementi del vettore la cui **somma sia esattamente T**. Stampa gli indici e i valori della coppia trovata, oppure un messaggio se non esiste.