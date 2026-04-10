<%*
const argomento = await tp.system.prompt("Argomento");
const keyword = await tp.system.prompt("Keyword");

const folder = tp.file.folder(true);

// legge file esistenti
const files = app.vault.getFiles()
  .filter(f => f.path.startsWith(folder + "/"))
  .map(f => f.basename);

// estrae numeri iniziali "NN - ..."
const nums = files
  .map(name => {
    const m = name.match(/^(\d+)\s*-/);
    return m ? parseInt(m[1]) : 0;
  });

const next = (Math.max(0, ...nums) + 1).toString().padStart(2,"0");

const nome = `${next} - ${argomento} - ${keyword}`;
await tp.file.rename(nome);
%>

# Esercizio — <% argomento %> <% keyword %>

tipo: esempio | guidato | rinforzo | compito | verifica
classe:
tempo:

## Testo

## Richieste

1.
2.
3.

## Soluzione