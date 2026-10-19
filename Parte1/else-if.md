# Il costrutto `else if`

## Teoria

Quando le alternative sono più di due, annidare `if-else` dentro altri `if-else` diventa rapidamente difficile da leggere. Il costrutto `else if` permette di scrivere catene di condizioni in modo lineare:

```c
if (condizione1) {
    /* ... */
} else if (condizione2) {
    /* ... */
} else if (condizione3) {
    /* ... */
} else {
    /* nessuna condizione precedente era vera */
}
```

Le condizioni vengono valutate **dall'alto verso il basso**: appena una è vera, il blocco corrispondente viene eseguito e tutte le successive vengono saltate.

Prima di vedere il codice, ecco i tre **operatori logici** che spesso compaiono nelle condizioni composte:

| Operatore | Significato | Esempio |
|-----------|-------------|---------|
| `&&` | AND — vero se *entrambi* sono veri | `eta >= 18 && eta <= 65` |
| `\|\|` | OR — vero se *almeno uno* è vero | `voto < 0 \|\| voto > 10` |
| `!` | NOT — inverte il valore logico | `!(a == b)` equivale a `a != b` |

## Implementazione in C

```c
/* Esempio — Classificazione di un voto scolastico */
#include <stdio.h>

int main(void) {
    int voto;

    printf("Inserisci il voto (0-10): ");
    scanf("%d", &voto);

    if (voto < 0 || voto > 10) {     /* input non valido: controlliamo subito */
        printf("Voto non valido.\n");
    } else if (voto == 10) {
        printf("Eccellente!\n");
    } else if (voto >= 8) {          /* qui sappiamo già che voto <= 9 */
        printf("Ottimo.\n");
    } else if (voto >= 6) {          /* qui sappiamo già che voto <= 7 */
        printf("Sufficiente.\n");
    } else if (voto >= 4) {          /* qui sappiamo già che voto <= 5 */
        printf("Mediocre.\n");
    } else {                         /* rimane solo voto in [0, 3] */
        printf("Gravemente insufficiente.\n");
    }

    return 0;
}
```

I commenti evidenziano un aspetto importante: poiché le condizioni si escludono a vicenda grazie all'ordine, ogni `else if` parte già con alcune certezze sul valore di `voto`. Questa osservazione diventa cruciale negli esercizi di ottimizzazione.

> [!CAUTION]
> **Attenzione all'errore — L'ordine delle condizioni conta**
>
> Se scrivi `else if (voto >= 4)` *prima* di `else if (voto >= 8)`, uno studente con 9 verrebbe classificato come "Mediocre" — la prima condizione è già vera e le successive vengono saltate. Parti sempre dai casi più restrittivi o specifici, oppure dai valori più alti se stai confrontando intervalli numerici.
