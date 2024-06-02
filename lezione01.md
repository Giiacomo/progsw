# Collaborative tools

## Version control

E' un sistema che permette di registrare le modifiche e tornare a stati precedenti del programma. Permette anche di collaborare con altri, permettendo di controllare chi ha fatto le modifiche e quando. 
Tra gli altri vantaggi abbiamo che:
- Ci forza anche all'uso di **development flows** ben conosciuti (es _DevOps_). 
- Ci fornisce un insieme di tool che rendono automatico il _testing_, l'_integrazione_ e lo _sviluppo_
- Ci fornisce un modo semplice di scrivere _documentazione_

## Git

Creato da _Linus Torvalds_ per supportare il kernel linux nel 2005.

Da qualche parte / su un cloud c'è una **repository remota** contenente il codice, chiamata **origin**. Gli _users_ possono **clonare** la repository in locale sulla loro macchina e tenere traccia degli update facendo il **pull** dalla repo in remoto. Possono inoltre caricare le loro modifiche facendo il **push**.

### Workflow di git

Un progetto è un insieme di **commits**:
- Sono degli snapshot (istantanee) del codice in un dato momento
- Si creano con _git commit_ 
- La granularità del commit dipende da chi lo fa, tipicamente è consigliato fare un commit dopo poche modifiche che riguardano una funzionalità comune

Ogni commit si riferisce ad un _parent commit_ e sono identificati da un **hashcode**. Il commit più recente è detto **HEAD** ed è obbligatorio aggiungere un commento a ogni commit.

Due comandi utili per controllare stato e differenze tra i commit sono:
- _git log_
- _git diff_

Per lavorare con i commit bisogna seguire i seguenti step:
- Prima di fare un commit bisogna aggiungere i file alla **staging area** con _git add files_
- Poi si può committare con _git commit -m "messaggio"_
- Per controllare la staging area _git status_

Una volta finito si può fare il push verso l'_origin_, bisogna però essere sicuri di essere all'ultima versione, quindi in ordine:
- _git pull_
- _git push -u origin master_

E' molto semplice fare casini se due codebase sono molto diverse e le si vuole unire, infatti git lavora a livello di code line. Se ci sono merge conflicts la repo locale è in **conflicting state**, fino a quando non si fa merge manuale e si risolvono tutti i conflitti. 

### Useful commands

- _checkout_ per togliere dallo stage modifiche e o commit
- _revert_ per tornare a un commit

### Project structure

Un progetto tipico è strutturato in maniera rigida:
- Un main branch, anche detto **master**, che contiene l'ultima versione rilasciata
- Diversi branch che corrispondono a lavori specifici/subprojects.

Solitamente non si può pushare direttamente sul master, ma si apre una pull request che dev'essere accettata da chi gestisce la repo.

Dopo aver fatto merge in locale, viene creato il commit finale e siamo pronti per fare push sul cloud e pull request, con mail o automated tools.

Per escludere alcuni file che non andrebbero aggiunti, come immagini o file generati automaticamente dall'ide (es \_\_pycache\_\_ e .vscode) si utilizza il file *.gitignore*.

Si può includere una repo git come una parte di un'altra repo attraverso il comando _git submodule add \<repo url\>_