# I puntatori

## Teoria

Ogni variabile in memoria occupa una certa quantità di byte a partire da un **indirizzo** — un numero che identifica la posizione fisica in memoria. Pensa alla memoria RAM come a una lunga strada con le case numerate: ogni casa è una cella di memoria, e l'indirizzo è il numero civico.

Un **puntatore** è una variabile il cui valore è un indirizzo di memoria. Non contiene un numero intero, un float o un carattere: contiene la posizione in cui trovare un'altra variabile.

*Memoria RAM (schema semplificato):*

|Indirizzo | Contenuto | Nome variabile | Note |
|----------|-----------|----------------|------|
|  0x1A00  |    42     |  x   (int)     | |
|  0x1A04  |  0x1A00   |  p   (int*)    | p è un puntatore: contiene l'indirizzo di x |
| 0x1A08 |   ...     | | |


I due operatori fondamentali per lavorare con i puntatori sono:

| Operatore | Nome | Significato |
|-----------|------|-------------|
| `&` | *address-of* | Restituisce l'indirizzo di una variabile |
| `*` | *dereference* | Accede al valore all'indirizzo puntato |

## Sintassi

```c
int x = 42;        /* variabile intera */
int *p = &x;       /* p è un puntatore a int; &x è l'indirizzo di x */

printf("%d\n", x);  /* stampa 42 — il valore di x */
printf("%p\n", p);  /* stampa l'indirizzo di x (es. 0x1A00) */
printf("%d\n", *p); /* dereferenzia p: accede al valore all'indirizzo → 42 */

*p = 100;           /* modifica il valore all'indirizzo puntato da p */
printf("%d\n", x);  /* stampa 100 — x è cambiata! */
```

> [!TIP]
> **Analogia — Il puntatore come numero civico**
>
> Immagina che `x` sia una cassetta delle lettere in Via della Memoria, al numero civico `0x1A00`. Il valore di `x` è il contenuto della cassetta. Il puntatore `p` è un bigliettino su cui è scritto `"Via della Memoria, 0x1A00"`. Con `*p` sei come un postino che legge il bigliettino, va a quell'indirizzo e guarda dentro la cassetta. Con `*p = 100` il postino non legge — *scrive* dentro la cassetta.

## Dichiarazione e uso dei puntatori

```c
/* Esempio — Puntatori: operatori & e * */
#include <stdio.h>

int main(void) {
    int eta = 17;
    int *ptr_eta = &eta;    /* ptr_eta punta a eta */

    printf("Valore di eta:           %d\n",  eta);
    printf("Indirizzo di eta (&eta): %p\n",  (void*)&eta);
    printf("Valore di ptr_eta:       %p\n",  (void*)ptr_eta);  /* stesso indirizzo */
    printf("Dereferenziazione *ptr:  %d\n",  *ptr_eta);    /* stesso valore di eta */

    /* Modifica tramite puntatore */
    *ptr_eta = 18;
    printf("\nDopo *ptr_eta = 18:\n");
    printf("eta vale ora: %d\n", eta);   /* eta è diventata 18 */

    return 0;
}
```

> [!CAUTION]
> **Attenzione all'errore — Il puntatore non inizializzato**
>
> ```c
> int *p;      /* p contiene un indirizzo casuale (spazzatura) */
> *p = 42;     /* PERICOLO: stai scrivendo all'indirizzo 0xC8F3...? */
> ```
> Usare un puntatore non inizializzato è uno degli errori più gravi in C: il programma potrebbe crashare con un *segmentation fault*, oppure — peggio — corrompere silenziosamente altre variabili. Inizializza sempre i puntatori: se non hai ancora un indirizzo da assegnargli, usa `NULL` (`int *p = NULL;`) e controlla prima di dereferenziare.
