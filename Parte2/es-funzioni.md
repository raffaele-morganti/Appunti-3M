# Esercizi proposti

## Base ★☆☆

### Cubo e quadrato

Scrivi due funzioni `quadrato` e `cubo` che ricevano un intero e restituiscano rispettivamente il suo quadrato e il suo cubo. Nel `main`, leggi un numero e stampa entrambi i risultati.

> [!NOTE]
> **Approfondimento**
> 
> scrivi una terza funzione `potenza(int base, int esp)` che calcoli `base` elevato a `esp` usando un ciclo. Può sostituire le prime due? Cosa succede se `esp` è 0? E se è negativo?

### Scambio verificato

Scrivi la funzione `scambia(int *a, int *b)` e testala nel `main` su tre coppie di valori diversi, stampando i valori prima e dopo ogni scambio per verificarne il corretto funzionamento.

### Conversione di temperatura

Scrivi le funzioni `celsius_to_fahrenheit(float c)` e `fahrenheit_to_celsius(float f)` che effettuino le conversioni tra le due scale. Le formule sono:
- °F = °C × 9/5 + 32
- °C = (°F − 32) × 5/9

Nel `main`, mostra una tabella di conversione da 0°C a 100°C con passo di 10°C.

### Conversioni tra temperature

Scrivi una funzione  `celsius_to_others(float c, float *f, float *k)` che effettui le conversioni di una temperatura fornita in Celsius nelle scale Fahrenheit e Kelvin secondo le formule:

- °F = °C × 9/5 + 32
- °K = °C + 273.15

Nel `main`, leggi un numero e stampa entrambi i risultati.

## Intermedio ★★☆

### Minimo, massimo e media

Scrivi una funzione `statistiche(int a, int b, int c, int *min, int *max, float *media)` che calcoli in un'unica chiamata minimo, massimo e media di tre interi, restituendo i risultati tramite puntatori. Testala nel `main`.

> [!NOTE]
> **Approfondimento**
> 
> modifica la funzione in modo che riceva anche un quarto puntatore `int *range` e calcoli il *range* (differenza tra massimo e minimo). Quanti parametri totali ha ora la funzione? A partire da quando una funzione con molti parametri diventa difficile da usare?

### Fattoriale iterativo

Scrivi una funzione `fattoriale(int n)` che calcoli n! (il fattoriale di n, ricordando che $n!=1\times2\times\dots\times n-1\times n$) utilizzando una versione **iterativa** (con un ciclo `for`).

### Fattoriale ricorsivo

Scrivi una funzione `fattoriale(int n)` che calcoli n! (il fattoriale di n) utilizzando una funzione **ricorsiva** (ovvero che chiama se stessa).

La funzione ricorsiva dovrà restituire:

- `fattoriale(0) = 1` (caso base)
- `fattoriale(n) = n * fattoriale(n-1)` (passo ricorsivo)

## Avanzato ★★★

### Generatore di numeri pseudo-casuali

Scrivi una funzione `generatore_lcg(int *seed)` che implementi un algoritmo di generazione di numeri pseudo-casuali di tipo LCG (Linear Congruential Generator). La funzione deve aggiornare il valore del seed usando la formula $X_{n+1} = (A \cdot X_n + C) \pmod M$. Dove $A=25173$, $C = 13849$ e $M = 2^{15} = 32768$.

Nel `main`, chiedi all'utente un valore iniziale (il seed), quindi chiama la funzione in un ciclo per generare e stampare a schermo i primi 10 numeri pseudo-casuali estratti.

> [!NOTE]
> **Approfondimento**
> 
> I numeri generati dall'algoritmo sono sempre minori di $32768$. Scrivi una funzione che utilizzi il tipo `unsigned long` e i valori $A=1103515245$, $C = 12345$ e $M = 2^{31} = 2147483648$. Lo specificatore da utilizzare nelle funzioni `scanf()` e `printf()` è `%lu`

### Numeri casuali in un intervallo specifico

Scrivi una funzione `rand_range(int *seed, int min, int max)` che utilizzi la funzione dell'esercizio precedente per restituire un numero casuale compreso esclusivamente nell'intervallo [min, max] (es. per simulare il lancio di un dado tra 1 e 6). Per generare numeri diversi ad ogni esecuzione inizializza il `seed` nel `main` usando l'ora corrente del sistema (usando la libreria <time.h>).