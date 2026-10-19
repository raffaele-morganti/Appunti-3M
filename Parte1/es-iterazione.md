# Esercizi proposti

## Base ★☆☆

### Tabellina interattiva

Scrivi un programma che legga un numero intero `n` e stampi la sua tabellina da 1 a 10 usando un ciclo `for`.

### Somma delle cifre

Scrivi un programma che legga un numero intero positivo e calcoli la **somma delle sue cifre** usando un ciclo `while`.

*(Suggerimento: `n % 10` restituisce l'ultima cifra di `n`; `n / 10` rimuove l'ultima cifra.)*

### Validazione con `do-while`

Scrivi un programma che chieda all'utente di inserire una password (un numero intero) e continui a richiedergliela finché non inserisce il valore corretto (sceglilo tu nel codice, es. `1234`). Conta i tentativi e stampane il numero al termine.

### Numeri di Fibonacci

La sequenza di Fibonacci inizia con 0 e 1; ogni termine successivo è la somma dei due precedenti: 0, 1, 1, 2, 3, 5, 8, 13, 21, …

Scrivi un programma che legga un intero `n` e stampi i primi `n` termini della sequenza.

## Intermedio ★★☆

### Indovina il numero

Scrivi un programma che "pensi" a un numero compreso tra uno e mille (usando `rand() % 1000 + 1`, dalla libreria `<stdlib.h>`) e chieda all'utente di indovinarlo. Ad ogni tentativo, indica se il numero inserito è troppo alto, troppo basso o corretto. Il ciclo termina quando l'utente indovina. Conta e stampa il numero di tentativi.

> [!NOTE]
> **Approfondimento — Ricerca binaria**
>
> Rifletti su quanti sarebbero i tentativi necessari per indovinare il numero se l'utente giocasse in modo ottimale.

### Disegna un triangolo

Scrivi un programma che legga un intero `n` (da 1 a 20) e stampi un triangolo rettangolo di `n` righe fatto di asterischi, come nel seguente esempio per `n = 5`:

```
*
**
***
****
*****
```

Poi stampa il triangolo **rovesciato** (5 stelle, poi 4, poi 3, …).

### Numero primo

Scrivi un programma che legga un intero positivo maggiore di 1 e stabilisca se è **primo** (divisibile solo per 1 e per se stesso).

*(Suggerimento: prova a dividerlo per tutti gli interi da 2 fino a `n-1`. Se trovi un divisore, non è primo.)*

> [!NOTE]
> **Approfondimento — Arresto ottimale**
> 
> Chiediti se sia davvero necessario arrivare fino a `n-1` o se sia possibile fermarsi già prima.

## Avanzato ★★★

### Collatz

La **congettura di Collatz** afferma che partendo da qualsiasi intero positivo `n` e applicando ripetutamente la regola:
- Se `n` è pari → `n = n / 2`
- Se `n` è dispari → `n = 3 * n + 1`

si arriva sempre a 1 (ma nessuno lo ha ancora dimostrato formalmente per tutti i numeri!).

Scrivi un programma che legga un intero positivo, simuli la sequenza di Collatz e stampi ogni passo. Conta e stampa il numero di passi necessari per raggiungere 1.

### Il giocatore d'azzardo

Un giocatore entra in un casinò con un budget iniziale di 10€. Decide di tentare il tutto per tutto alla roulette europea: punta sempre 1€ sul suo numero fortunato. Se esce quel numero guadagna 35€, altrimenti perde l'euro puntato. Il giocatore smetterà solo se raggiunge 100€ o se rimane al verde.

Scrivi un programma che simuli questa sessione di gioco usando un ciclo. Ad ogni iterazione, genera un numero casuale tra 0 e 36 (usando `rand() % 37`, dalla libreria `<stdlib.h>`). Se il numero generato corrisponde al numero del giocatore, allora la puntata è vinta, altrimenti persa. Il programma deve stampare quanti lanci sono stati necessari e l'esito finale.

> [!NOTE]
> **Approfondimento — La legge dei grandi numeri**
>
> racchiudi l'intero blocco di simulazione dentro un secondo ciclo più esterno per simulare la stessa  esperienza per 1.000.000 giocatori contemporaneamente. Il programma non dovrà mostrare i singoli lanci, ma dovrà calcolare e mostrare alla fine:
>
> 1. La percentuale giocatori usciti vincitori.
> 2. L'incasso complessivo del casinò.
