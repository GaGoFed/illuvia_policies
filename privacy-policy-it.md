# Illuvia — Informativa sulla privacy

**Ultimo aggiornamento: 6 agosto 2026 · Vale per Illuvia 1.0.0 per Windows**

## In breve

Illuvia non raccoglie nulla. Non ha server, non ha account, non ha strumenti di
analisi e non apre alcuna connessione di rete per conto proprio. Tutto quello
che scrivi resta in file sul tuo PC, sotto il tuo account Windows.

## Cosa salva Illuvia, e dove

Tutto quello che inserisci — attività, checklist, transazioni, conti, piani di
pagamento, desideri, veicoli, impostazioni — finisce in file nella tua cartella
utente:

```
%APPDATA%\Gagofed\Illuvia\database\
```

È quella cartella sia che Illuvia arrivi dal Microsoft Store sia che venga
eseguita da una build normale: i dati non stanno dentro il pacchetto installato.

Quei file sono **cifrati su disco** con AES-256. La chiave viene generata sul tuo
PC al primo avvio e custodita nella Gestione credenziali di Windows, protetta
per il tuo account Windows (DPAPI). Non deriva mai dal tuo PIN o dalla tua
password, e non lascia mai la macchina. Chi copiasse i file su un altro PC, o
provasse a leggerli da un altro account Windows, non riuscirebbe a decifrarli.

Illuvia scrive anche un registro diagnostico in chiaro:

```
%APPDATA%\Gagofed\Illuvia\logs\illuvia.log
```

Annota cosa ha fatto l'app — quale modulo si è caricato, quanti record ha letto,
cosa diceva un errore — così che un problema si possa capire a posteriori. È
limitato a 5 MB con al massimo tre file di rotazione, non viene mandato da
nessuna parte e puoi cancellarlo quando vuoi. Non è cifrato: se lo invii per
avere assistenza, leggilo prima.

## Cosa Illuvia non fa

- **Nessuna raccolta di dati.** Nessuna statistica d'uso, nessuna segnalazione
  di crash, nessuna analisi, nessuna pubblicità, nessuna profilazione, nessun
  identificativo di alcun tipo.
- **Nessun account.** Non c'è niente da registrare e non serve un indirizzo
  e-mail per usare l'app.
- **Nessuna rete.** Il pacchetto dell'app non dichiara alcuna capability di
  connessione a Internet e l'applicazione non fa richieste. Funziona con il cavo
  di rete staccato.
- **Nessun terzo.** Niente di quello che inserisci viene condiviso con qualcuno,
  perché non c'è nessuno con cui condividerlo.

## Le due volte in cui qualcosa esce dall'app

**Aprire un link.** Se salvi il link di un negozio su un desiderio, o usi il link
per la donazione, toccandolo l'indirizzo viene passato al tuo browser
predefinito. Da quel momento sei su quel sito, sotto la sua informativa, non
sotto questa. Illuvia non scarica la pagina.

**Fare un backup.** Un backup è un unico file che contiene tutto, salvato dove
scegli tu. Come esce dal computer lo decidi tu:

- **Esporta senza password** (predefinito). Il file viene scritto come JSON leggibile.
  È l'unico modo per ispezionare un backup o per aprirlo con qualcosa che non sia
  Illuvia, ed è privato esattamente quanto il posto in cui lo metti. Se hai
  salvato le credenziali di un servizio su un piano di pagamento (vedi sotto),
  Illuvia ti avvisa prima di scrivere: lì dentro sono in chiaro.
- **Esporta con password.** Il file viene sigillato con AES-256, con una chiave
  derivata dalla tua password (Argon2id). Può essere ripristinato su qualsiasi
  macchina, e senza quella password non si apre: nessuno può recuperarla per te.

Le copie che Illuvia scrive per sé — quelle automatiche, e la copia di sicurezza
presa prima di un ripristino o di un import — sono sempre sigillate con la chiave
di questo PC. Restano nella cartella di Illuvia, e disinstallare l'app le lascia
lì insieme a tutto il resto.

## Le password che salvi per altri servizi

Un piano di pagamento può contenere nome utente e password del servizio che paga
— il tuo account della luce, un abbonamento — perché è lì che li cerchi. Sono
salvati come ogni altro campo: nel database, cifrati a riposo, solo su questo PC.
Non vengono mai inviati da nessuna parte, e Illuvia non ha modo di usarli.

Ne seguono due cose. Viaggiano dentro un backup, ed è ciò che permette a un
ripristino di rimettere i tuoi dati com'erano; e quindi un'**esportazione non
protetta** li contiene in chiaro, ed è per questo che Illuvia avvisa prima di
scriverla.

## Il blocco dell'app

Il PIN o la password che aprono Illuvia sono un'altra cosa, e non vengono mai
memorizzati. Viene memorizzato
un hash Argon2id, con un salt casuale, nella Gestione credenziali di Windows
accanto alla chiave di cifratura. Windows Hello, se lo attivi, è gestito
interamente da Windows: Illuvia riceve solo un sì o un no e non vede mai dati
biometrici.

## Cancellare i tuoi dati

Impostazioni → Sicurezza → *Svuota tutti i moduli* elimina tutto quello che hai
inserito. Accanto, *Cancella tutti i dati* rimuove anche la chiave di cifratura e la
credenziale: è quello che fa il flusso "ho dimenticato il PIN".

**Disinstallare Illuvia non cancella i tuoi dati.** Windows rimuove
l'applicazione e lascia le cartelle indicate sopra dove sono, così reinstallando
ritrovi tutto com'era. Se vuoi che spariscano anche i dati, usa prima uno dei due
comandi, oppure cancella tu la cartella `%APPDATA%\Gagofed\Illuvia\`: lì dentro stanno il
database, il log e le copie automatiche.

I backup che hai esportato non vengono toccati da nessuna di queste operazioni:
solo tu sai dove sono.

## Minori

Illuvia è un organizzatore personale di uso generale. Non è rivolta ai minori e
non raccoglie informazioni da nessuno, di nessuna età.

## Modifiche a questa informativa

Se una versione futura di Illuvia dovesse cambiare quello che fa con i tuoi
dati, questa pagina verrà aggiornata prima che quella versione venga
pubblicata, e la modifica sarà descritta nelle note di rilascio.

## Contatti

Domande su questa informativa: **illuvia.dev@gmail.com**
