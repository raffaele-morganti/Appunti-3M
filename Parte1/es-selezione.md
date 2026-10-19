# Esercizi proposti

## Base ★☆☆

### Positivo, negativo o zero

Scrivi un programma che legga un numero intero e stampi se è **positivo**, **negativo** o **zero**.

### Accesso al cinema

Un cinema applica prezzi diversi in base all'età:
- Under 10 e over 70: **gratuito**
- Da 10 a 17 anni: **€5,00**
- Da 18 a 70 anni: **€9,50**

Scrivi un programma che legga l'età e stampi il prezzo del biglietto. Gestisci anche il caso di un'età non valida (negativa o superiore a 120).

### Anno bisestile

Un anno è bisestile se è divisibile per 4, **tranne** i centenari (divisibili per 100) che sono bisestili solo se divisibili anche per 400. Ad esempio: 2000 → bisestile, 1900 → non bisestile, 2024 → bisestile.

Scrivi un programma che legga un anno e stabilisca se è bisestile.

## Intermedio ★★☆

### Triangolo: validità e tipo

Scrivi un programma che legga tre lati (interi) e:
1. Verifichi se formano un triangolo valido *(ogni lato deve essere strettamente minore della somma degli altri due)*.
2. Se valido, classifichi il triangolo in **equilatero**, **isoscele** o **scaleno**.

### Massimo tra quattro numeri

Scrivi un programma che legga **quattro** numeri interi e stampi il massimo.

Inizia con la soluzione più diretta (una serie di confronti).

> [!NOTE]
> **Approfondimento — Ottimizzazione**
>
> Rifletti su quanti confronti stai effettuando e chiediti se è possibile ridurli.

## Avanzato ★★★

### Validazione di una data

Scrivi un programma che legga una data nel formato `giorno mese anno` e stabilisca se è **valida**, tenendo conto di:
- Mesi con 31 giorni: 1, 3, 5, 7, 8, 10, 12.
- Mesi con 30 giorni: 4, 6, 9, 11.
- Febbraio: massimo 29 giorni negli anni bisestili.

Stampa un messaggio chiaro che indichi se la data è valida e, in caso contrario, il motivo dell'errore.
