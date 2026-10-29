# Le funzioni

## Teoria

Una **funzione** è un sottoprogramma: un insieme di istruzioni raggruppate sotto un nome, che riceve degli **argomenti** in ingresso (i *parametri*) e produce un **risultato** in uscita (il *valore di ritorno*).

Pensa a una funzione come a una macchinetta del caffè: inserisci una cialda e una moneta (parametri), la macchina esegue il suo processo interno, e ottieni un caffè (valore di ritorno). Non ti interessa sapere esattamente come funziona il meccanismo interno — ti interessa l'interfaccia: cosa dai, cosa ottieni.

Questo principio si chiama **astrazione** ed è uno dei pilastri della programmazione moderna.

In C ogni funzione ha:
- Un **tipo di ritorno** — il tipo del valore restituito (`int`, `float`, `void` se non restituisce nulla).
- Un **nome** — identificatore con cui la si chiama.
- Una **lista di parametri** — le variabili che riceve in ingresso.
- Un **corpo** — il blocco di istruzioni che esegue.

## Sintassi

```c
tipo_ritorno nome_funzione(tipo1 param1, tipo2 param2, ...) {
    /* corpo */
    return valore;   /* obbligatorio se tipo_ritorno != void */
}
```

> [!WARNING]
> **Attenzione all'errore — dichiarazione della funzione**
>
> poiché il compilatore C legge il codice dall'alto verso il basso, non puoi usare una funzione prima che questa sia stata dichiarata.
>
> - Se definisci la funzione interamente prima dell'utilizzo, non ci sono problemi.
>
> - Se definisci la funzione dopo il suo utilizzo, devi obbligatoriamente inserire una dichiarazione preventiva (chiamata prototipo o firma, es: `tipo_ritorno nome_funzione(tipo1 param1, tipo2 param2, ...);`). In caso contrario, il compilatore non "vedrà" la funzione durante la lettura del codice e genererà un errore di compilazione.

## Implementazione in C

```c
/* Esempio — Funzioni matematiche di base */
#include <stdio.h>

/* Dichiarazione (prototipo): informa il compilatore dell'esistenza
   della funzione prima che venga usata nel main */
int massimo(int a, int b);
int minimo(int a, int b);
int valore_assoluto(int n);

int main(void) {
    int x = -7, y = 3;

    printf("x = %d, y = %d\n", x, y);
    printf("Massimo:           %d\n", massimo(x, y));
    printf("Minimo:            %d\n", minimo(x, y));
    printf("Valore assoluto x: %d\n", valore_assoluto(x));

    return 0;
}

/* Definizione delle funzioni — dopo il main */

int massimo(int a, int b) {
    if (a > b) {
        return a;
    } else {
        return b;
    }
}

int minimo(int a, int b) {
       if (a < b) {
        return a;
    }
    return b;
}

int valore_assoluto(int n) {
    if (n < 0) {
        n = -n;
    }
    return n;
}
```

> [!TIP]
> **Curiosità — Prototipo vs definizione**
>
> In C il compilatore legge il file dall'alto verso il basso. Se chiami una funzione prima di averla definita, il compilatore non sa quanti parametri aspettarsi né che tipo restituisce. Il **prototipo** (o *dichiarazione forward*) risolve questo problema: è una riga che descrive la "firma" della funzione senza il corpo. La **definizione** (con il corpo completo) può stare più in basso nel file. In progetti grandi, i prototipi vanno nei file `.h` (header).

**Funzioni `void` — quando non si restituisce nulla:**

```c
/* Esempio — Funzione che stampa un separatore visivo */
#include <stdio.h>

/* Nessun valore di ritorno: tipo void */
void stampa_linea(int lunghezza, char carattere) {
    for (int i = 0; i < lunghezza; i++) {
        printf("%c", carattere);
    }
    printf("\n");
}

int main(void) {
    stampa_linea(30, '=');
    printf("   REPORT VENDITE\n");
    stampa_linea(30, '=');
    printf("Prodotto A: €1.200\n");
    printf("Prodotto B: €  850\n");
    stampa_linea(30, '-');
    printf("Totale:     €2.050\n");

    return 0;
}
```

Output:
```
==============================
   REPORT VENDITE
==============================
Prodotto A: €1.200
Prodotto B: €  850
------------------------------
Totale:     €2.050
```

> [!WARNING]
> **Attenzione all'errore — Variabili locali e scope**
>
> Le variabili dichiarate all'interno di una funzione sono **locali**: esistono solo durante l'esecuzione di quella funzione e vengono distrutte al termine. Se due funzioni hanno una variabile locale chiamata `i`, sono due variabili completamente indipendenti. Non esiste rischio di "interferenza" tra funzioni — ma questo significa anche che una funzione non può modificare direttamente una variabile del chiamante. Per farlo, servono i puntatori.
