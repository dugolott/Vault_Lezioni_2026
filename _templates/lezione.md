<%*  
const titolo = await tp.system.prompt("Argomento lezione");  
if (!titolo) {  
new Notice("Creazione annullata: nessun argomento inserito.");  
return;  
}  
  
const data = tp.date.now("YYYY-MM-DD");  
const nomeFile = `${data} ${titolo}`;  
  
const currentPath = tp.file.path(true);  
const currentFolder = tp.file.folder(true);  

const cart = `currP = ${currentPath}\n currF = ${currentFolder}`;
new Notice(cart); 


const folderParts = currentFolder.split("/");  
  
const classe = folderParts.length > 0 ? folderParts[0] : "";  
const materia = folderParts.length > 1 ? folderParts[1] : "";  
const sezione = folderParts.length > 2 ? folderParts[2] : "";  
  
if (sezione !== "Lezioni") {  
new Notice("Attenzione: crea la nota dentro una cartella .../Lezioni");  
}  
  
// se il file è stato creato in root, lo sposta nella cartella corrente desiderata  
const nuovoPath = `${currentFolder}/${nomeFile}.md`;  
if (currentPath !== nuovoPath) {  
await app.fileManager.renameFile(tp.file.find_tfile(currentPath), nuovoPath);  
}  
  
// crea cartella img dentro Lezioni, se manca  
const imgFolder = `${currentFolder}/img`;  
if (!(await app.vault.adapter.exists(imgFolder))) {  
await app.vault.createFolder(imgFolder);  
}  
%>
# <% data %> — <% titolo %>  
  
tags: [lezione]  
classe: <% classe %>  
materia: <% materia %>  
  
## Argomento  
<% titolo %>  
  
## Obiettivi  
-  
  
## Spiegazione  
-  
  
## Attività  
-  
  
## Materiali  
-  
  
## Compiti  
-  
  
## Note  
-  
  
## Immagini  
  
![schema](img/schema.png)