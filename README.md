<p align="center">
  <img src="assets/images/Comma.png" width="350" align="center"/>
</p><br>

Sistema di autenticazione PHP di facile integrazione e sicurezza elevata con login, registrazione, profili utente, modifica profilo, verifica dell'account via e-mail, sistema di reimpostazione della password, funzione Ricordami, disconnessione automatica in caso di inattivitÃ , variabile di stato e di errore globali, controlli di autenticazione.

# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Getting Started](#getting-started)
    - [Requirements](#requirements)
    - [Installation](#installation)
    - [Existing Account(s)](#existing-accounts)
    - [Project File Structure](#project-file-structure)
    - [Building on top of System](#building-on-top-of-system)
  - [Components](#components)
    - [Languages](#languages)
    - [Development Environment](#development-environment)
    - [External Resources/Plugins](#external-resourcesplugins)
  - [Features](#features)
    - [Easy Integration / Embedding](#easy-integration--embedding)
    - [Security](#security)
      - [SQL Injection Protection](#sql-injection-protection)
      - [Header & Email Injection Protection](#header--email-injection-protection)
      - [CSRF Protection](#csrf-protection)
      - [Secure Remember-me Cookie](#secure-remember-me-cookie)
      - [Secure Account Activation & Password Reset](#secure-account-activation--password-reset)
    - [Login | Signup](#login--signup)
    - [Automatic Logout on Inactivity](#automatic-logout-on-inactivity)
    - [User Profile | Profile Editing](#user-profile--profile-editing)
    - [Email Verification | Account Activation](#email-verification--account-activation)
    - [Password Resetting](#password-resetting)
    - [Auth Verification](#auth-verification)
    - [Remember Me Feature](#remember-me-feature)
    - [GLOBAL temporary ERROR & STATUS values](#global-temporary-error--status-values)
    - [Contact System](#contact-system)
  - [Future Improvements](#future-improvements)
  - [Contribution Guidelines](#contribution-guidelines)
  - [License](#license)
  - [Personal Note](#personal-note)

## Getting Started

### Requirements
* PHP
* Apache server
* MySQL
* PHPMailer
* Bootstrap
* JQuery 

### Installation
1. Importa il file 'assets/setup/db.sql' nel DBMS (PhpMyAdmin). Il file dump crea il database, quindi nessun tipo di azione Ã© richiesta. Se si vuole aggiornare il nome del database, cambialo nel file dump dove il database Ã© dichiarato.
2. Modifica il file `assets / setup / env.php` e configura le informazioni dell'applicazione, la connessione al database e il server SMTP. Il valore della porta di solito non Ã¨ necessario nelle connessioni al database, quindi modifica solo se sai cosa stai facendo. Il server di posta elettronica (e l'account di posta elettronica collegato) verrÃ  utilizzato per inviare email di conferma, validazione e notifica.
```php
// env.php

if (!defined('APP_NAME'))                       define('APP_NAME', 'Comma Application');
if (!defined('APP_ORGANIZATION'))               define('APP_ORGANIZATION', 'Comma');
if (!defined('APP_OWNER'))                      define('APP_OWNER', '');
if (!defined('APP_DESCRIPTION'))                define('APP_DESCRIPTION', 'Embeddable PHP Login System');

if (!defined('ALLOWED_INACTIVITY_TIME'))        define('ALLOWED_INACTIVITY_TIME', time()+1*60);

if (!defined('DB_DATABASE'))                    define('DB_DATABASE', 'pcto');
if (!defined('DB_HOST'))                        define('DB_HOST','127.0.0.1');
if (!defined('DB_USERNAME'))                    define('DB_USERNAME','root');
if (!defined('DB_PASSWORD'))                    define('DB_PASSWORD' ,'123456');
if (!defined('DB_PORT'))                        define('DB_PORT' ,'');

if (!defined('MAIL_HOST'))                      define('MAIL_HOST', 'smtp.gmail.com');
if (!defined('MAIL_USERNAME'))                  define('MAIL_USERNAME', 'pcto.5id@gmail.com');
if (!defined('MAIL_PASSWORD'))                  define('MAIL_PASSWORD', 'pcto_cl5ID');
if (!defined('MAIL_ENCRYPTION'))                define('MAIL_ENCRYPTION', 'ssl');
if (!defined('MAIL_PORT'))                      define('MAIL_PORT', 465);
```
### Existing Account(s)
Il database contiene giÃ  accounts di prova per testare le cose. Usalo o vai alla pagina di registrazione e inizia a creare nuovi account.

### Project File Structure

  
| Path / File | Purpose  |
| -- | -- | 
| `[accessible URLs/Pages]`     | Tutti i folder nella directory root, tranne quello chiamato `assets`. |
| `assets/css`                  | Cartelle per i file CSS personalizzati globali o specifici per il layout. |
| `assets/images`               | Le immagini utilizzate nell'interfaccia utente dell'applicazione o nel file README di git. |
| `assets/includes`             | Funzioni o classi. |
| `assets/js`                   | Custom javascript files. |
| `assets/setup`                | File di configurazione e di setup del progetto. |
| `assets/uploads`              | Cartella per tutti i contenuti caricati dagli utenti dell'applicazione. |
| `assets/uploads/users`        | Immagini caricate dagli utenti. |
| `assets/vendor`               | Cartella per tutti i plugin / risorse. |

### Building on top of System

Una volta impostato questo sistema di autenticazione, puÃ² essere facilmente ampliato in questo modo: le nuove pagine possono essere aggiunte rapidamente creando piÃ¹ cartelle nella directory principale, con il file principale frontend che Ã¨ `index.php`, le funzionalitÃ  backend nella sottocartella` includes` e lo stile personalizzato nel file` custom.css`, presente nella stessa cartella di livello superiore di index.php.

Nuovi gruppi di funzioni o classi possono essere creati in nuovi file nella cartella`assets/includes/` e devono essere inclusi nelle pagine relevanti. se le funzionalitÃ  aggiunte sono in gran parte universali, possono essere richiesti nel file` assets/layouts/header.php` (questo li include per tutti i file frontend, ma i file backend dovranno ancora essere collegati singolarmente). Allo stesso modo, altri file CSS globali possono essere salvati nella cartella` assets/css` e inclusi nel file di layout header.php. La stessa convenzione si applicherÃ  ai file JS, con gli script che saranno nella cartella` assets/js /` e inclusi nel file` assets/layouts/footer.php`.

Ulteriori plugin o risorse offline possono essere collocati nella cartella`assets/vendor/` e collegati nel file di layout header o footer, a seconda del tipo di file da collegare.

> Una buona convenzione da adottare durante la costruzione sul sistema sarebbe adottare le stesse convenzioni di struttura dei file come in questo sistema, al fine di evitare uno sforzo extra e / o inutile per sincronizzare l'intero progetto. Il sistema Ã¨ giÃ  stato realizzato con la struttura di file di applicazione PHP di default al fine di evitare la maggior parte dei conflitti.

## Components

### Languages

- PHP
- MySQLi API
- HTML5
- CSS3

### Development Environment

- Apache
- Ubuntu

### External Resources/Plugins

- PHPMailer-6.0.6
- Bootstrap-4.3.1
- Font awesome-5.12.0
- JQuery-3.4.1

## Features

### Easy Integration / Embedding

L'applicazione Ã¨ progettata per essere facilmente incorporabile e deve essere realizzata su di essa. L'attuale interfaccia utente Ã¨ stata creata per lo piÃ¹ con bootstrap. Lo scopo di questo progetto Ã¨ fornire la funzionalitÃ  `backend` necessaria, e tutti gli elementi dell'interfaccia utente dovrebbero essere sostituiti e / o ricostruiti quando si crea un'applicazione separata.

Si raccomanda di installare / incorporare l'applicazione nel progetto prima della creazione dell'applicazione `backend` (e preferibilmente dell'applicazione frontend). In caso contrario, se la struttura dei file esistente Ã¨ in conflitto con quella di questo progetto, potrebbero verificarsi problemi e sarÃ  difficile sincronizzare nuovamente l'intero progetto.

Il progetto Ã¨ stato creato con la struttura standard dei file di sviluppo PHP, per mantenere la flessibilitÃ . Aggiungi semplicemente altre funzionalitÃ  / pagine nello stesso modo in cui sono state create le cartelle di pagina di esempio nella cartella principale.

In ciascuna cartella di pagina, il file `index.php` Ã¨ la pagina principale, la cartella `includes` contiene la funzionalitÃ  backend e il file `custom.css` consente disegni personalizzati su un file css globale senza interferire con altre pagine.
### Security

#### SQL Injection Protection

Il sistema utilizza "mysqli prepared statements" per tutte le interazioni con il database, eliminando la maggior parte dei rischi di SQL injection. Non Ã¨ stato usato alcun query SQL raw in nessuna parte, inoltre, tutti i dati inseriti dall'utente vengono verificati e controllati prima di essere utilizzati in qualsiasi funzionalitÃ  dell'applicazione. Di conseguenza si intensificano ulteriormente le misure di sicurezza.

```php
// example database query

$sql = "DELETE FROM auth_tokens WHERE user_email=? AND auth_type='account_verify';";
$stmt = mysqli_stmt_init($conn);
if (!mysqli_stmt_prepare($stmt, $sql)) {

    $_SESSION['ERRORS']['sqlerror'] = 'SQL ERROR';
    header("Location: ../");
    exit();
}
else {

    mysqli_stmt_bind_param($stmt, "s", $email);
    mysqli_stmt_execute($stmt);
}
```

#### Header & Email Injection Protection

L'applicazione utilizza la funzione `_cleaninjections()` definita in `assets/includes/security_functions.php` per filtrare e convalidare i dati. Qualsiasi dato inserito dagli utenti per qualsiasi funzionalitÃ  viene controllato per l'iniezione di intestazione prima di essere utilizzato. Le funzioni di filtro rimuovono qualsiasi carattere (s) che potrebbe rivelarsi una minaccia, rendendo cosÃ¬ innocui qualsiasi script o dati dannosi.

In tutte le funzionalitÃ  di back, ogni singolo valore incluso nella posta viene controllato per eventuali injection. Lo stesso vale per le email, impedendo agli utenti di aggiungere campi di posta elettronica aggiuntivi. CiÃ² riduce notevolmente il rischio di injection di intestazione o di email.

```php
// Securing against Header Injection

foreach($_POST as $key => $value){

  $_POST[$key] = _cleaninjections(trim($value));
}
```
#### CSRF Protection

C'Ã¨ anche una pesante protezione contro gli tentativi di CSRF. Un `token csrf` sicuro viene generato all'avvio della sessione e inviato come valore nascosto nel corpo del post per tutti i moduli, in cui viene convalidato e consente allo script di procedere solo se la convalida riesce. La protezione csrf funziona per tutti i moduli, indipendentemente dal fatto che l'utente sia collegato o meno.

Il token csrf Ã¨ gestito dalle funzioni presenti nel file `assets/includes/security_functions.php`. Il token viene crittografato per impedirne l'estrazione e l'utilizzo.
```php
// csrf token generation

function generate_csrf_token() {
  if (!isset($_SESSION)) {
      session_start();
  }
  if (empty($_SESSION['token'])) {
      $_SESSION['token'] = bin2hex(random_bytes(32));
  }
}
```
#### Secure Remember-me Cookie

Il cookie impostato per la funzionalitÃ  `remember-me` utilizza valori `selector` e `validator` crittografati che impediscono interferenze o exploit. Il token stesso non viene memorizzato cosÃ¬ com'Ã© nel database, eliminando il rischio di fuoriuscita di informazioni in caso di violazione del database. Il token di autenticazione e il selettore sono memorizzati nella tabella `auth_tokens` del database.

#### Secure Account Activation & Password Reset

Le funzionalitÃ  per l'attivazione dell'account e il ripristino della password utilizzano entrambe un link inviato via email che utilizza anche valori `selector` e `validator` crittografati. Tutti e tre i livelli, ovvero i cookie remember-me, l'attivazione dell'account e il ripristino della password utilizzano la tabella `auth_tokens` per archiviare i token crittografati e il selettore. Ognuno dei token ha un tempo di scadenza, il che significa che una volta scaduti, non possono essere utilizzati. Tutti i token vengono eliminati all'utilizzo, quindi non possono essere utilizzati piÃ¹ e piÃ¹ volte.

### Login | Signup

Il sistema supporta un sistema di login e registrazione predefinito e sicuro. L'utente puÃ² registrarsi per creare un nuovo account e verrÃ  quindi invitato a effettuare il login sul nuovo account con le sue credenziali. L'utente puÃ² anche impostare la sua immagine del profilo durante la registrazione. Per creare un nuovo account, l'utente deve impostare un nome utente univoco e un indirizzo email. Sono disponibili anche altri campi di informazione, ma sono facoltativi e possono essere saltati.

Il sistema di login supporta anche una funzionalitÃ  `ricordami`, che manterrÃ  l'utente collegato per un certo periodo di tempo (attualmente un mese) anche se il browser o il sistema verranno spenti.

### Automatic Logout on Inactivity

L'applicazione contiene un frammento di codice jquery in `assets / js / check_inactive.js` che controlla continuamente se l'utente Ã¨ inattivo. Quando l'utente Ã¨ inattivo per piÃ¹ del tempo specificato, esegue automaticamente il logout e reindirizza alla pagina di login. Il periodo di inattivitÃ  consentito Ã¨ attualmente `1 hr`, specificato in `assets / setup / env.php` nella costante `ALLOWED_INACTIVITY_TIME`. Lo script js chiama lo script in `assets / includes / checkinactive.ajax.php` tramite chiamata AJAX, dove viene controllata l'inattivitÃ  dell'utente.

```php
// checkinactive.ajax.php

session_start();
if (isset($_SESSION['auth']) && !isset($_COOKIE['rememberme'])){
    if(time() > $_SESSION['expire']){
        session_unset();
        session_destroy();
        echo 'logout_redirect';
    }
}
```
### User Profile | Profile Editing // da vedere se i dati utente corrispondono con quelli di rigon

Il sistema supporta un profilo utente corretto accessibile alla registrazione. Attualmente sono stati inseriti nel database solo pochi campi di informazioni aggiuntive, ovvero il nome, il cognome, il sesso, il titolo del profilo e la biografia dell'utente. Questi sono solo destinati a dimostrare l'utilizzo di ulteriori informazioni sull'utente e, pertanto, sono campi opzionali che possono essere saltati durante la registrazione. L'utente ha anche un'immagine del profilo che puÃ² scegliere / impostare alla registrazione e puÃ² anche aggiornarla in seguito.

C'Ã¨ anche un sistema di aggiornamento del profilo, in cui l'utente puÃ² aggiornare tutte le sue informazioni. Nel sistema attuale, l'utente deve avere un nome utente univoco e un indirizzo email, quindi il sistema conferma la disponibilitÃ  del nuovo nome utente o dell'email se sono stati modificati per l'aggiornamento del profilo.

> Il sistema puÃ² anche aggiornare l'immagine del profilo dell'utente e cancellare l'immagine precedente successivamente per evitare inutili accumuli di immagini nel file system del server.

C'Ã¨ anche un controllo separato per l'aggiornamento della password, che richiede all'utente di inserire la password attuale e di confermare la nuova password. Una volta aggiornata la password, viene inviata all'utente un'email di notifica all'indirizzo email attuale.

### Email Verification | Account Activation

Al momento della signup / registrazione, il sistema consente all'utente l'accesso al nuovo account, ma con accesso limitato. Con la registrazione avvenuta con successo, viene inviata una e-mail di conferma all'indirizzo e-mail dell'utente, contenente un link di verifica sicuro. Una volta acceduto al link, l'account viene sbloccato / attivato e l'utente puÃ² accedere a tutte le funzionalitÃ  aggiuntive. Il link viene creato con i campi `selector` e `token` crittografati, mentre nella relativa voce viene creata una voce nel database per la verifica ogni volta che viene acceduto il link.

Il campo del database che determina se l'account Ã¨ verificato / sbloccato o meno Ã¨ `verified_at`. Se il campo Ã¨ NULL, l'account non Ã¨ verificato. L'email di verifica inviata all'utente imposta quel valore di colonna con la data / l'ora correnti in quel momento, sbloccando cosÃ¬ l'account.

Al momento del login, lo script controlla il campo `verified_at` e imposta il valore di `$ _SESSION ['auth']` di conseguenza. Se l'utente non Ã¨ verificato, verrÃ  reindirizzato alla pagina `APPLICATION_PATH / verify` in cui verrÃ  chiesto di attivare il proprio account con l'email inviata. Nel caso in cui l'utente non abbia ricevuto l'email, Ã¨ prevista un'opzione per consentirgli di inviare nuovamente quell'email. Una volta attivato l'account e aggiornata la pagina, l'utente verrÃ  reindirizzato lontano dalla pagina di verifica alla pagina `APPLICATION_PATH / home` predefinita.

### Password Resetting

C'Ã¨ anche un sistema di reimpostazione della password, o per la terminologia ben nota, una funzione `password dimenticata?`. Il link a quella funzione Ã¨ presente nella pagina di login sotto il modulo di login e richiede che l'utente inserisca la sua email con cui si Ã¨ registrato. Se l'email non Ã¨ presente nel database, la richiesta viene ignorata e, se presente, viene inviata all'utente un'email di conferma altamente sicura. L'utente puÃ² accedere al link fornito in quell'email, che lo costringerÃ  a ricreare la propria password e, una volta fatto, gli verrÃ  richiesto di effettuare l'accesso con le nuove credenziali.

L'e-mail di conferma / ripristino utilizza la tabella `auth_tokens` nel database per creare un sicuro `selector` e `token` per l'utente, quindi li aggiunge al link di ripristino dopo l'encryption. Il token ha un certo tempo di scadenza (attualmente `1 ora`), dopo il quale diventa invalido.

### Auth Verification

Il sistema gestisce i controlli di autenticazione con l'aiuto di funzioni specifiche memorizzate in `assets/includes/auth_functions.php`. Ci sono diverse funzioni per determinare lo stato corrente dell'utente. E i controlli possono essere applicati a qualsiasi pagina in una sola volta semplicemente richiamando la funzione rispettiva in cima al file.


Le funzioni di autenticazione disponibili (al momento) sono:
```php
function check_logged_in() { ... }
function check_logged_in_butnot_verified() { ... }
function check_logged_out() { ... }
function check_verified() { ... }
function check_remember_me() { ... }
function force_login($email) { ... }
```
Ogni pagina puÃ² essere impostata per accettare gli utenti in un determinato stato semplicemente chiamando la funzione corrispondente nella parte superiore del file.

```php
// Home page, only meant for verified users

define('TITLE', "Home");
include '../assets/layouts/header.php';
check_verified();
```
### Remember Me Feature

Il sistema di login presenta una funzione `remember me`, che tiene l'utente collegato anche se il browser o il dispositivo viene spento. Durante il login, se l'utente ha selezionato l'opzione `rememer me`, la funzione imposta un cookie sicuro con valori `selector` e `token` crittografati e crea i rispettivi valori nella tabella `auth_tokens` del database.

```php
$selector = bin2hex(random_bytes(8));
$token = random_bytes(32);
setcookie(
  'rememberme',
  $selector.':'.bin2hex($token),
  time() + 864000,
  '/',
  NULL,
  false, 
  true  
);
```
Per convalidare il cookie, il sistema utilizza la funzione `check_remember_me()` nell'file `assets/includes/auth_functions.php`. Una volta verificati i valori crittografati contro quelli memorizzati nel database, chiama il metodo `force_login()` che crea semplicemente le variabili di sessione relative all'utente e lo fa accedere all'applicazione.

### GLOBAL temporary ERROR & STATUS values

Il progetto utilizza una variabile di STATO e ERRORI globali per eventuali errori e stato della pagina, assegnati come un array associativo a $_SESSION ['ERRORS'] e $_SESSION ['STATUS'], con le chiavi che sono nomi di errore / stato e i valori sono i messaggi. Questi valori sono temporanei, il che significa che i valori di errore scompaiono quando la pagina viene aggiornata, riportando la pagina allo stato originale. CiÃ² mantiene gli URL puliti (senza usare le query URL) e l'array associativo significa che in caso di qualsiasi errore, una nuova chiave con qualsiasi nome puÃ² essere creata e dato il messaggio di errore come valore e potrebbe essere facilmente gestita nei file frontend.

Un esempio di creazione di un errore e l'assegnazione di `$_SESSION ['ERRORS']` in uno script backend Ã¨:

```php
// checking email availability

if ($_SESSION['email'] != $email && !availableEmail($conn, $email)) {

  $_SESSION['ERRORS']['emailerror'] = 'email already taken';
  header("Location: ../");
  exit();
}
```

Similmente, questo Ã¨ il modo in cui si puÃ² accedere all'errore sul file di frontend visibile:

```html
// profile update form with email field

<div class="form-group">
  <label for="email">Email address</label>
  <input type="email" id="email" name="email" ... >
  <sub class="text-danger">
    <?php
        if (isset($_SESSION['ERRORS']['emailerror']))
            echo $_SESSION['ERRORS']['emailerror'];
    ?>
  </sub>
</div>
```

### Contact System

L'applicazione ha un semplice sistema di contatto che utilizza il server di posta impostato in `assets/setup/env.php` per inviare una email a se stessa, contenente le informazioni del mittente, oltre al messaggio. Il modulo di contatto Ã¨ accessibile sia quando si Ã¨ loggati che quando non lo si Ã¨. Quando non si Ã¨ loggati, richiede il nome e l'email del mittente. E quando si Ã¨ loggati, utilizza il nome utente e l'email dell'utente corrente per inviare la mail di contatto.
Il sistema utilizza un modello di email per inviare le email, che puÃ² essere aggiornato, migliorato o sostituito.

## Future Improvements

Ci sono alcune cose che ho in mente per aggiungere a questo progetto in futuro. Tuttavia, questo Ã¨ un impegno che potrei o non potrei essere in grado di mantenere. Se uno di voi finisce per migliorare in modo significativo questo progetto, sarebbe un onore per me contribuire a questo progetto.

Detto ciÃ², queste sono alcune migliorie possibili che ho in mente adesso:

- Login OAuth. (login tramite applicazioni di terze parti come gmail o github ecc.).
- Requisito per la conferma della posta con nuovo indirizzo per l'aggiornamento email.
- Mantieni una colonna `data` nella tabella `users` del database con testo codificato in JSON e sposta i campi extra come nome, cognome, bio e headline ecc. nel database. CiÃ² renderebbe la tabella piÃ¹ gestibile e creerebbe maggiore flessibilitÃ  per aggiungere piÃ¹ campi di dati in formato JSON.
- FunzionalitÃ  grezza di un semplice pannello di amministrazione, con una semplice lista di tutti gli utenti con funzionalitÃ  per:
  - Cerca un utente.
  - Filtra utenti.
  - Elimina utenti.
  - Attiva / disattiva gli utenti (impostando manualmente la loro colonna `verified_at` su NULL o sulla data / ora corrente).
  - Crea utenti.
  - Aggiorna le informazioni critiche (e forse anche quelle critiche).
- Opzione per eliminare l'account, con la conferma via email che Ã¨ necessaria per farlo.
- Immagini di copertina per gli utenti.
- Livelli di utente assegnati alla registrazione (amministratore, utente normale ecc.) E sistema di autorizzazioni per questo.
- Invio di e-mail tramite script AJAX in background per ridurre i tempi di esecuzione degli script.
- Controllo della password in tempo reale con JQuery.
- Un file universale con regole di convalida per tutte le input dell'utente.

## Contribution Guidelines

If you want to contribute to this project, please refer to the [Contributing Guidelines](CONTRIBUTING.md).

## License
Questo progetto Ã¨ stato assegnato il [MIT License](LICENSE), quindi sentiti libero di utilizzare qualsiasi e/o tutte le parti di questo sistema e di costruirvi sopra. Anche se insisterrei ancora che, se dovessi effettivamente migliorarlo, dovessi contribuire accidentalmente, sarebbe un onore.

## Personal Note


           
