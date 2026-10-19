# Il costrutto `if-else`

## Teoria

Spesso non ci basta definire cosa fare *se* una condizione è vera: vogliamo anche un comportamento alternativo *quando è falsa*. Entra in scena `if-else`:

> *"Se la condizione è vera, fai A; altrimenti fai B."*

Uno dei due rami viene **sempre** eseguito — mai entrambi, mai nessuno.

## Sintassi

```c
if (condizione) {
    /* eseguito se condizione è VERA */
} else {
    /* eseguito se condizione è FALSA */
}
```

## Implementazione in C

```c
/* Esempio — Numero pari o dispari */
#include <stdio.h>

int main(void) {
    int n;

    printf("Inserisci un numero intero: ");
    scanf("%d", &n);

    if (n % 2 == 0) {           /* % è l'operatore modulo: resto della divisione */
        printf("%d è pari.\n", n);
    } else {
        printf("%d è dispari.\n", n);
    }

    return 0;
}
```

> [!TIP]
> **Curiosità — L'operatore modulo `%`**
>
> `n % 2` restituisce il resto della divisione intera di `n` per 2. Se il resto è 0 il numero è pari, altrimenti è dispari. L'operatore modulo è utilissimo: permette di verificare divisibilità, far "avvolgere" i contatori (es. ore dell'orologio con `% 24`) e molto altro ancora.

## `if-else` annidati

È possibile mettere un `if-else` dentro un altro `if-else` per gestire situazioni più articolate. Si parla di **annidamento** (*nesting*).

```c
/* Esempio — Simulazione prelievo bancomat */
#include <stdio.h>

int main(void) {
    float saldo, prelievo;

    printf("Saldo attuale (€): ");
    scanf("%f", &saldo);
    printf("Importo da prelevare (€): ");
    scanf("%f", &prelievo);

    if (prelievo <= 0.0f) {               /* primo controllo: importo valido? */
        printf("Errore: l'importo deve essere positivo.\n");
    } else {                              /* l'importo è positivo... */
        if (prelievo > saldo) {           /* secondo controllo: fondi sufficienti? */
            printf("Operazione negata: saldo insufficiente.\n");
            printf("Saldo disponibile: €%.2f\n", saldo);
        } else {                          /* tutto ok: esegui il prelievo */
            saldo = saldo - prelievo;
            printf("Prelievo di €%.2f effettuato.\n", prelievo);
            printf("Nuovo saldo: €%.2f\n", saldo);
        }
    }

    return 0;
}
```

Nota come l'annidamento rispecchi la logica reale di uno sportello bancomat: prima si verifica che l'importo abbia senso, *poi* si controlla se ci sono fondi sufficienti. Invertire i controlli non sarebbe sbagliato, ma sarebbe meno naturale.

> [!WARNING]
> **Attenzione all'errore — L'indentazione non cambia la logica**
>
> In C, le indentazioni sono solo per la leggibilità umana: il compilatore le ignora completamente. Se dimentichi le graffe, un'istruzione che visivamente sembra dentro un `if` potrebbe in realtà essere fuori. Usa sempre le graffe.
