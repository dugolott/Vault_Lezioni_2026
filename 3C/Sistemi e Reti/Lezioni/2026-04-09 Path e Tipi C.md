# 10/04 — Variabili di ambiente e tipi in C

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

#### Floating point (IEEE 754)
| Tipo         | Bit |
|--------------|-----|
| float        | 32  |
| double       | 64  |
| long double* | 80/128 |

Nota:
- La FPU esegue i calcoli alla massima precisione disponibile (>=80 bit)

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

---

### Gestione errori con valori sentinella

Definizione:
```
#include <limits.h>

#define ERRORE1 INT_MAX
#define ERRORE2 INT_MIN
```

Uso:
```
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
- Stampare i limiti dei tipi usando limits.h , sizeof() 

## Materiali  
- Compilatore C (gcc / MinGW)  
- Terminale  

## Compiti  
- Scrivere un programma che stampi i limiti dei tipi  
- Testare differenze tra signed e unsigned  

## Note  
- I tipi possono variare per architettura  
- Usare sempre <limits.h> invece di valori hardcoded  

## Immagini  
