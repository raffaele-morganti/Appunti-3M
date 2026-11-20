# Funzioni e vettori

## Teoria

Quando passi un array a una funzione, in realtà stai passando un puntatore al suo primo elemento — **non una copia dell'intero array**. Questo ha due conseguenze importanti:

1. La funzione **può modificare** gli elementi dell'array originale (come il passaggio per indirizzo).
2. La funzione **non sa** quanto è grande l'array: la dimensione va passata esplicitamente come parametro separato.

## Sintassi

```c
/* Queste due dichiarazioni sono equivalenti per il compilatore */
void funzione(int arr[], int n);
void funzione(int *arr, int n);
```

La prima forma (`int arr[]`) è più leggibile e comunica chiaramente l'intenzione; la seconda (`int *arr`) è più esplicita sulla natura del passaggio. Entrambe sono corrette ma noi useremo la prima forma per chiarezza.

## Implementazione in C — Algoritmi classici sui vettori

```c
/* Esempio — Somma e media degli elementi */
#include <stdio.h>

/* Calcola la somma degli elementi di un vettore di n interi */
int somma(int arr[], int n) {
    int tot = 0;
    for (int i = 0; i < n; i++) {
        tot += arr[i];
    }
    return tot;
}

/* Calcola la media degli elementi */
float media(int arr[], int n) {
    if (n == 0) return 0.0f;          /* caso limite: array vuoto */
    return (float)somma(arr, n) / n;  /* cast a float per evitare divisione intera */
}

int main(void) {
    int voti[] = {6, 8, 7, 9, 5, 7, 8};
    int n = 7;

    printf("Somma:  %d\n", somma(voti, n));
    printf("Media:  %.2f\n", media(voti, n));

    return 0;
}
```

```c
/* Esempio — Ricerca lineare */
#include <stdio.h>

/*
 * Cerca il valore target nel vettore arr di n elementi.
 * Restituisce l'indice della prima occorrenza, oppure -1 se non trovato.
 * -1 è una convenzione comune in C per indicare "non trovato" con gli indici.
 */
int ricerca_lineare(int arr[], int n, int target) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == target) {
            return i;    /* trovato: restituisce subito l'indice */
        }
    }
    return -1;           /* non trovato */
}

int main(void) {
    int numeri[] = {15, 3, 42, 8, 27, 16, 4};
    int n = 7;
    int cerca = 27;

    int pos = ricerca_lineare(numeri, n, cerca);

    if (pos != -1) {
        printf("%d trovato alla posizione %d\n", cerca, pos);
    } else {
        printf("%d non presente nel vettore\n", cerca);
    }

    return 0;
}
```

> [!TIP]
> **Curiosità — Perché -1 come "non trovato"?**
>
> Gli indici validi di un array vanno da `0` a `n-1`, quindi `-1` è un valore impossibile come indice — una scelta naturale per segnalare l'assenza. Questa convenzione è così diffusa che la ritroverai in molte librerie C e in altri linguaggi. In alternativa, alcune funzioni restituiscono un puntatore (`NULL` per "non trovato").

```c
/* Esempio — Minimo, massimo e loro posizioni */
#include <stdio.h>

int indice_minimo(int arr[], int n) {
    int idx_min = 0;                 /* assumi che il minimo sia il primo */
    for (int i = 1; i < n; i++) {    /* parti da 1: il confronto con 0 è già fatto */
        if (arr[i] < arr[idx_min]) {
            idx_min = i;             /* aggiorna l'indice del minimo */
        }
    }
    return idx_min;
}

int indice_massimo(int arr[], int n) {
    int idx_max = 0;
    for (int i = 1; i < n; i++) {
        if (arr[i] > arr[idx_max]) {
            idx_max = i;
        }
    }
    return idx_max;
}

int main(void) {
    int temp[] = {22, 19, 25, 31, 28, 17, 24};
    int n = 7;

    int i_min = indice_minimo(temp, n);
    int i_max = indice_massimo(temp, n);

    printf("Minimo: %d (posizione %d)\n", temp[i_min], i_min);
    printf("Massimo: %d (posizione %d)\n", temp[i_max], i_max);

    return 0;
}
```
