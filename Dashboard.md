# Dashboard docente

## Tutte le lezioni

```dataview
TABLE file.folder as Classe, file.name as Lezione
FROM ""
WHERE contains(file.path,"Lezioni")
SORT file.name DESC
```

## Tutti gli argomenti

```dataview
LIST
FROM ""
WHERE contains(file.path,"Argomenti")
SORT file.name
```
