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

### Existing Account(s)
Il database contiene già un account di prova per testare le cose. Usalo o vai alla pagina di registrazione e inizia a creare nuovi account.
```php
// credentials for existing account

username: root
password: root
```

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
           
            
