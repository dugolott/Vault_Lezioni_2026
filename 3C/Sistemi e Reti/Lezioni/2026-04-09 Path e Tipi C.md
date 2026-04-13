#2026-04-09 — Variabili di ambiente e tipi in C

tags: [lezione]
classe: 3C INF
materia: Informatica

## Argomento

- Variabile d'ambiente PATH
- tipi nativi del linguaggio C

## Obiettivi

- Comprendere il ruolo delle variabili di ambiente
- Saper modificare la variabile PATH
- Conoscere i tipi primitivi del C
- Comprendere range e rappresentazione dei numeri
- Comprendere il legame tra Tipi e Architettura Compilatore
- Gestire errori tramite valori sentinella

## Spiegazione

### Variabile PATH

La variabile di ambiente PATH contiene l'elenco dei percorsi in cui il sistema operativo cerca gli eseguibili.

- Permette di eseguire programmi da qualsiasi directory
- I percorsi sono separati da `;` (Windows)

Esempio:

```
C:\Windows\System32;C:\Program Files\...
```

#### Modifica del PATH

- **Persistente**: pannello di controllo → variabili d’ambiente
- **Temporanea (shell)**:

```
set PATH=%PATH%;C:\Program Files\CodeBlocks\MinGW\bin
```

Nota:
- `%PATH%` mantiene i percorsi esistenti
- Non dimenticare il `;` come separatore

---

### Tipi nativi del C

#### Interi (codifica complemento a 2)

| Tipo      | Bit | Range signed    | Range unsigned |
| --------- | --- | --------------- | -------------- |
| char      | 8   | -128 .. 127     | 0 .. 255       |
| short     | 16  | -32768 .. 32767 | 0 .. 65535     |
| int°      | 32  | ~ -2G .. +2G    | 0 .. ~4G       |
| long      | 32  | ~ -2G .. +2G    |                |
| long long | 64  | ~ -9E .. +9E    | 0 .. ~18E      |

(°) dipendente dall'architettura

Attenzione:
- Windows: int e long sono entrambi 32 bit
- A seconda dell'architettura e del compilatore, i tipi possono variare in dimensione e range; in particolare le opzioni di compilazione possono influenzare la dimensione dei tipi (es. -m32 vs -m64)
- Per la stampa dei tipi interi usare `%d` (signed) o `%u` (unsigned)
- Per tipi più grandi di int usare `%lld` (signed) o `%llu` (unsigned) ...purtroppo non è supportato da windows che richiede `%I64d` e `%I64u`
- L'opzione di compilazione -D__USE_MINGW_ANSI_STDIO abilita il supporto per i formati di stampa standard anche su Windows


#### Floating point (IEEE 754)

| Tipo         | Bit |
|--------------|-----|
| float        | 32  |
| double       | 64  |
| long double* | 80/128 |

Nota:
- La FPU esegue i calcoli alla massima precisione disponibile (>=80 bit)
- la stampa di float e double è con `%f` o `%e` (notazione esponenziale)
- long double è supportato solo su alcune piattaforme e compilatori, e la sua dimensione può variare; in molti casi è implementato come 80 bit (extended precision) o 128 bit (quadruple precision), ma non è garantito

---

### Signed vs Unsigned

- `signed` è implicito
- `unsigned`:
  - elimina i numeri negativi
  - raddoppia il range positivo

Esempio:

```
unsigned int x; // solo valori >= 0
```
### sizeof()

- Operatore che restituisce la dimensione in byte di un tipo o variabile
- Esempio:

```c
printf("Dimensione di int: %zu byte\n", sizeof(int));
```

- Restituisce il valore di tipo `size_t`, che è un tipo intero senza segno (a 32 o 64 bit) utilizzato per rappresentare dimensioni e conteggi; per stampare correttamente questo tipo, si usa `%zu` come specificatore di formato (al solito non supportato da Windows che richiede `%Iu`)

Esercizio:
Scrivere un programma che stampi dimensione e range dei tipi nativi usando `<limits.h>` , `<float.h>`e `sizeof()`

Svolgimento:
```c
#include <stdio.h>
#include <limits.h>
#include <float.h>

int main(){
    printf("Dimensione di char: %zu byte, range signed: %d .. %d, range unsigned: 0 .. %d\n", sizeof(char), SCHAR_MIN, SCHAR_MAX, UCHAR_MAX);
    printf("Dimensione di short: %zu byte, range signed: %d .. %d, range unsigned: 0 .. %d\n", sizeof(short), SHRT_MIN, SHRT_MAX, USHRT_MAX);
    printf("Dimensione di int: %zu byte, range signed: %d .. %d, range unsigned: 0 .. %u\n", sizeof(int), INT_MIN, INT_MAX, UINT_MAX);
    printf("Dimensione di long: %zu byte, range signed: %ld .. %ld\n", sizeof(long), LONG_MIN, LONG_MAX);
    printf("Dimensione di long long: %zu byte, range signed: %lld .. %lld, range unsigned: 0 .. %llu\n", sizeof(long long), LLONG_MIN, LLONG_MAX, ULLONG_MAX);
    printf("Dimensione di float: %zu byte, precisione: ~%d cifre decimali\n", sizeof(float), FLT_DIG);
    printf("Dimensione di double: %zu byte, precisione: ~%d cifre decimali\n", sizeof(double), DBL_DIG);
    printf("Dimensione di long double: %zu byte, precisione: ~%d cifre decimali\n", sizeof(long double), LDBL_DIG);

    return 0;
}
```
---

### Gestione errori con valori sentinella

Definizione:

```c
#include <limits.h>

#define ERRORE1 INT_MAX
#define ERRORE2 INT_MIN
```

Uso:

```c
int index = calcola_indice(100);

if(index != ERRORE1)
{
    // uso valido
}
else
{
    printf("\nErrore di calcolo");
}
```

Nota:
- Come codici di errore dobbiamo sempre usare valori fuori dal dominio valido
- attenzione a non confonderli con risultati reali

---

## Attività
- Verificare il PATH del proprio sistema
- Aggiungere un percorso temporaneo da shell
- Stampare dimensione e limiti dei tipi nativi usando limits.h, float.h e sizeof()

## Materiali
- Compilatore C (gcc / MinGW)
- Terminale

## Compiti

- Completare l'esercizio verificando dimensione e range dei tipi unsigned
- Compilare il sorgente con compilatore a 32 e 64 bit e confrontare i risultati. Dovrete installare uno o più compilatori che forniscano il supporto per le architetture desiderate (es. MinGW-w64 per Windows, gcc con opzioni -m32 e -m64 su Linux)
- Sfida: trovare, installare e testare il codice con un compilatore a 16 bit (es. Small-C). Se riuscite fate uno screecast che mostri il processso dall'installazione alla compilazione e esecuzione del codice


## Note


## Immagini
