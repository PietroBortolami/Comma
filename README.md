<p align="center">
  <img src="assets/images/Comma.png" width="350" align="center"/>
</p><br>
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
1. Importa il file 'assets/setup/db.sql' nel DBMS (PhpMyAdmin). Il file dump crea il database, quindi nessun tipo di azione é richiesta. Se si vuole aggiornare il nome del database, cambialo nel file dump dove il database é dichiarato.
2. Modifica il file `assets / setup / env.php` e configura le informazioni dell'applicazione, la connessione al database e il server SMTP. Il valore della porta di solito non è necessario nelle connessioni al database, quindi modifica solo se sai cosa stai facendo. Il server di posta elettronica (e l'account di posta elettronica collegato) verrà utilizzato per inviare email di conferma, validazione e notifica.
```php
// env.php

if (!defined('APP_NAME'))                       define('APP_NAME', 'Comma Application');
if (!defined('APP_ORGANIZATION'))               define('APP_ORGANIZATION', 'Comma');
if (!defined('APP_OWNER'))                      define('APP_OWNER', '');
if (!defined('APP_DESCRIPTION'))                define('APP_DESCRIPTION', 'Embeddable PHP Login System');

if (!defined('ALLOWED_INACTIVITY_TIME'))        define('ALLOWED_INACTIVITY_TIME', time()+1*60);

if (!defined('DB_DATABASE'))                    define('DB_DATABASE', 'db');
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
Il database contiene già un account di prova per testare le cose. Usalo o vai alla pagina di registrazione e inizia a creare nuovi account.

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

Una volta impostato questo sistema di autenticazione, può essere facilmente ampliato in questo modo: le nuove pagine possono essere aggiunte rapidamente creando più cartelle nella directory principale, con il file principale frontend che è `index.php`, le funzionalità backend nella sottocartella` includes` e lo stile personalizzato nel file` custom.css`, presente nella stessa cartella di livello superiore di index.php.

Nuovi gruppi di funzioni o classi possono essere creati in nuovi file nella cartella`assets/includes/` e devono essere inclusi nelle pagine relevanti. se le funzionalità aggiunte sono in gran parte universali, possono essere richiesti nel file` assets/layouts/header.php` (questo li include per tutti i file frontend, ma i file backend dovranno ancora essere collegati singolarmente). Allo stesso modo, altri file CSS globali possono essere salvati nella cartella` assets/css` e inclusi nel file di layout header.php. La stessa convenzione si applicherà ai file JS, con gli script che saranno nella cartella` assets/js /` e inclusi nel file` assets/layouts/footer.php`.

Ulteriori plugin o risorse offline possono essere collocati nella cartella`assets/vendor/` e collegati nel file di layout header o footer, a seconda del tipo di file da collegare.

> Una buona convenzione da adottare durante la costruzione sul sistema sarebbe adottare le stesse convenzioni di struttura dei file come in questo sistema, al fine di evitare uno sforzo extra e / o inutile per sincronizzare l'intero progetto. Il sistema è già stato realizzato con la struttura di file di applicazione PHP di default al fine di evitare la maggior parte dei conflitti.

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

L'applicazione è progettata per essere facilmente incorporabile e deve essere realizzata su di essa. L'attuale interfaccia utente è stata creata per lo più con bootstrap. Lo scopo di questo progetto è fornire la funzionalità `backend` necessaria, e tutti gli elementi dell'interfaccia utente dovrebbero essere sostituiti e / o ricostruiti quando si crea un'applicazione separata.

Si raccomanda di installare / incorporare l'applicazione nel progetto prima della creazione dell'applicazione `backend` (e preferibilmente dell'applicazione frontend). In caso contrario, se la struttura dei file esistente è in conflitto con quella di questo progetto, potrebbero verificarsi problemi e sarà difficile sincronizzare nuovamente l'intero progetto.

Il progetto è stato creato con la struttura standard dei file di sviluppo PHP, per mantenere la flessibilità. Aggiungi semplicemente altre funzionalità / pagine nello stesso modo in cui sono state create le cartelle di pagina di esempio nella cartella principale.

In ciascuna cartella di pagina, il file `index.php` è la pagina principale, la cartella `includes` contiene la funzionalità backend e il file `custom.css` consente disegni personalizzati su un file css globale senza interferire con altre pagine.
### Security

#### SQL Injection Protection

Il sistema utilizza "mysqli prepared statements" per tutte le interazioni con il database, eliminando la maggior parte dei rischi di SQL injection. Non è stato usato alcun query SQL raw in nessuna parte, inoltre, tutti i dati inseriti dall'utente vengono verificati e controllati prima di essere utilizzati in qualsiasi funzionalità dell'applicazione. Di conseguenza si intensificano ulteriormente le misure di sicurezza.

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

L'applicazione utilizza la funzione `_cleaninjections()` definita in `assets/includes/security_functions.php` per filtrare e convalidare i dati. Qualsiasi dato inserito dagli utenti per qualsiasi funzionalità viene controllato per l'iniezione di intestazione prima di essere utilizzato. Le funzioni di filtro rimuovono qualsiasi carattere (s) che potrebbe rivelarsi una minaccia, rendendo così innocui qualsiasi script o dati dannosi.

In tutte le funzionalità di back, ogni singolo valore incluso nella posta viene controllato per eventuali injection. Lo stesso vale per le email, impedendo agli utenti di aggiungere campi di posta elettronica aggiuntivi. Ciò riduce notevolmente il rischio di injection di intestazione o di email.

```php
// Securing against Header Injection

foreach($_POST as $key => $value){

  $_POST[$key] = _cleaninjections(trim($value));
}
```
#### CSRF Protection

C'è anche una pesante protezione contro gli tentativi di CSRF. Un `token csrf` sicuro viene generato all'avvio della sessione e inviato come valore nascosto nel corpo del post per tutti i moduli, in cui viene convalidato e consente allo script di procedere solo se la convalida riesce. La protezione csrf funziona per tutti i moduli, indipendentemente dal fatto che l'utente sia collegato o meno.

Il token csrf è gestito dalle funzioni presenti nel file `assets/includes/security_functions.php`. Il token viene crittografato per impedirne l'estrazione e l'utilizzo.
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

Il cookie impostato per la funzionalità `remember-me` utilizza valori `selector` e `validator` crittografati che impediscono interferenze o exploit. Il token stesso non viene memorizzato così com'é nel database, eliminando il rischio di fuoriuscita di informazioni in caso di violazione del database. Il token di autenticazione e il selettore sono memorizzati nella tabella `auth_tokens` del database.
            
