# gfauser-26 · le consegne delle classi del prof. Garofalo

ITIS Fauser di Novara, anno scolastico **2026-27**. Materie: **TPSIT**, **Informatica**, **GPOI**.

Qui fai esercizi, compiti e verifiche con **Git**, **GitHub** e **`fauser`**, il programma della classe. È lo stesso modo di lavorare che troverai in un'azienda: scrivi il codice, lo provi, salvi la storia, lo invii.

---

## I repository e a cosa servono

| Repository | Chi lo vede | A cosa serve | Tu cosa fai |
|---|---|---|---|
| **`fauser-<username>`** | tu e il docente (privato) | **il tuo repository**: tutte le tue consegne, di tutte le materie, per tutto l'anno | ci lavori ogni giorno: clone, commit, push |
| [**`fauser`**](https://github.com/gfauser-26/fauser) | tutti | il programma `fauser`, da scaricare dalle [release](https://github.com/gfauser-26/fauser/releases/latest) | lo scarichi una volta e lo aggiorni quando il docente lo dice |
| [**`tracce`**](https://github.com/gfauser-26/tracce) | tutti | le tracce (`TRACCIA.md`) e i test pubblici di esercizi, compiti e verifiche | **niente**: le scarica `fauser nuovo` per te. Puoi leggerle qui |

Il **progetto personale** sta in un repository suo, a parte.

---

## Il flusso, in una figura

```text
   tracce (pubblico)                 il tuo computer                       fauser-<username> (privato)
 ┌──────────────────┐   fauser nuovo   ┌──────────────────────────┐  git push   ┌───────────────────────┐
 │ TRACCIA.md       │ ───────────────▶ │ src/   il tuo codice     │ ──────────▶ │ la tua consegna       │
 │ tests/ pubblici  │                  │ tests/ i casi pubblici   │             │ (vale l'ora del push) │
 └──────────────────┘                  │ fauser test → .esito     │             └───────────┬───────────┘
                                       └──────────────────────────┘                         │
                                                                                            ▼
                                             consegne-private (solo docente) ──▶ il docente rifà girare
                                             test nascosti                        test pubblici + nascosti
```

1. **`fauser nuovo <ID> --materia <materia>`** crea la cartella giusta e scarica traccia e test pubblici.
2. Scrivi il codice in **`src/`** e il **`README.md`** (con la sezione «Uso dell'AI»).
3. **`fauser test`** compila, prova ogni caso e scrive la ricevuta `.esito`.
4. **Commit piccoli** mentre lavori: `git commit -m "E01: leggo i due numeri"` e `git push`.
5. **`fauser consegna`** rilancia i test, fa il commit `<ID>: consegna` e il push.
---

## Il primo giorno (una volta sola)

1. Account GitHub con **nickname** (niente nome e cognome), **2FA attiva**, **email nascosta** (scheda A2 del progetto personale).
2. Su Discord: `/github collega`. Il docente ti invita in `gfauser-26`: accetta l'invito dall'email o da [github.com/notifications](https://github.com/notifications).
3. Installa **Git**, **VS Code**, il **compilatore** del tuo linguaggio e **`fauser`** (vedi il [README di fauser](https://github.com/gfauser-26/fauser#installazione) e la guida PDF).
4. Configura Git e clona il tuo repository:

```bash
git config --global user.name "<nickname>"
git config --global user.email "<la-tua-email-noreply>"   # finisce con @users.noreply.github.com
gh auth login                                              # oppure un token, vedi la guida
mkdir -p ~/scuola && cd ~/scuola
git clone https://github.com/gfauser-26/fauser-<username>.git
cd fauser-<username>
fauser lingua <linguaggio>                                 # c, cpp, csharp, java, python, go, ts, js
git add .fauser.json && git commit -m "Scelgo il linguaggio" && git push
```

---

## Il comando da ricordare

```bash
fauser consegna
```

Controlla nomi e struttura, fa girare i test, fa il commit e il push. Se qualcosa non va (nome della cartella, `lang.txt`, file principale, README vuoto, test che falliscono, push rifiutato) **si ferma e ti dice cosa correggere**. Se finisce con **`Consegnato: <ID>`** in verde, è arrivato tutto.

I **nomi** contano: il docente ricorregge in automatico, e un file con il nome sbagliato (`main.java` invece di `Main.java`, `Python` invece di `python`) vuol dire «consegna vuota». La tabella completa è nel [README di fauser](https://github.com/gfauser-26/fauser#i-nomi-da-rispettare).

---

## Le regole in breve

- **Un solo repository**, `fauser-<username>`, sempre sul ramo **`main`**. Niente rami, niente pull request.
- Le cartelle sono sempre `<materia>/2026-27/{esercizi,compiti,verifiche}/<ID>-<data>-<titolo>/`. Le crea `fauser`, non tu.
- **ID**: `E01` esercizio, `C01` compito, `V1` verifica. Li dà il docente nella traccia.
- **Otto linguaggi** ammessi: C, C++, C#, Java, Python, Go, TypeScript, JavaScript. Nelle verifiche puoi cambiarlo da un esercizio all'altro.
- Il programma legge da **standard input** e scrive su **standard output**, esattamente come chiede la traccia.
- **Non toccare** `tests/` e `.esito`.
- **La scadenza**: vale l'ora in cui GitHub ha ricevuto il **push**, non l'ora del commit. Un commit non inviato non esiste.
- Puoi consegnare più volte prima della scadenza: vale l'ultima. Con i test che falliscono: `fauser consegna --forza` e spiegalo nel README.
- **AI**: sì per capire, no per farti scrivere l'esercizio. Dichiarala sempre nel README. Devi saper spiegare il tuo codice **riga per riga**.
- Il codice di un compagno non si copia. Se prendi codice da un libro o da un sito, scrivi la **fonte**.
- **Mai** password, token, chiavi o dati personali nei file e nei commit. Se ti scappa, avvisa subito il docente.
- Il repository resta **privato**: non cambiare la visibilità.

---

## Piccoli trucchi con Git

| Ti serve | Comando |
|---|---|
| Cosa ho cambiato? | `git status`, poi `git diff` |
| Salvare un passo | `git add .` e `git commit -m "<ID>: cosa hai fatto"` |
| Inviare a GitHub | `git push` |
| Il push è rifiutato | `git pull --rebase`, poi `git push` |
| Ho sbagliato il messaggio (non ancora inviato) | `git commit --amend -m "<nuovo messaggio>"` |
| Vedere la storia | `git log --oneline` |
| Annullare le modifiche a un file (non salvate) | `git restore <file>` |
| Ho committato `node_modules`, `bin/`, `.exe` | `git rm -r --cached <cartella>`, commit, poi aggiungila a `.gitignore` |
| Mi sono perso in un rebase | `git rebase --abort` e chiedi aiuto |

> **Regola d'oro:** prima di cominciare, `git pull --rebase`. Quando qualcosa funziona, commit e push. Alla fine, `fauser consegna` e controlla su github.com che il commit ci sia.

---

## Per approfondire

- **Pro Git** in italiano, il libro ufficiale e gratuito: [git-scm.com/book/it/v2](https://git-scm.com/book/it/v2)
- **GitHub Docs** in italiano: [docs.github.com/it](https://docs.github.com/it/get-started)
- Il **cheat sheet** di GitHub Education: [education.github.com/git-cheat-sheet-education.pdf](https://education.github.com/git-cheat-sheet-education.pdf)
- Imparare Git **giocando**: [learngitbranching.js.org](https://learngitbranching.js.org/?locale=it_IT)
- Corsi interattivi di GitHub: [skills.github.com](https://skills.github.com/)
- Git in **VS Code**: [code.visualstudio.com/docs/sourcecontrol/overview](https://code.visualstudio.com/docs/sourcecontrol/overview)
- File `.gitignore` pronti per ogni linguaggio: [github.com/github/gitignore](https://github.com/github/gitignore)
- Il **GitHub Student Developer Pack** (strumenti gratuiti per studenti): [education.github.com/pack](https://education.github.com/pack)

Hai un problema? Prima leggi la sezione «Quando qualcosa va storto» della guida PDF, poi chiedi su Discord o al docente. Scrivi **cosa hai fatto**, **cosa ti aspettavi** e **l'errore esatto** (copiato, non fotografato), mai password o token.
