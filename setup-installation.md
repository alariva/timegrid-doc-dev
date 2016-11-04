# Installation

- [Minimum system requirements](#system-requirements)
- [Command-line Installation steps](#command-line-installation)
- [Post-installation steps](#post-install-steps)
    - [Setting up the scheduler](#crontab-setup)

Before you proceed, you should check that your server meets the minimum system requirements.

<a name="system-requirements"></a>
## Minimum system requirements

timegrid has some server requirements for web hosting:

1. PHP >= 5.5.9
1. OpenSSL PHP Extension
1. PDO PHP Extension
1. Mbstring PHP Extension
1. Tokenizer PHP Extension
1. Nginx or Apache web server
1. MySQL server

> **Advice:** PHP 7 is not yet supported.

> As of PHP 5.5, some OS distributions may require you to manually install the PHP JSON extension.
When using Ubuntu, this can be done via ``apt-get install php5-json``.

<a name="command-line-installation"></a>
## Command-line installation

* [Step 1: Get the code](#step1)
* [Step 2: Use Composer to install dependencies](#step2)
* [Step 3: Create Database](#step3)
* [Step 4: Install](#step4)
* [Step 5: Start Page](#step5)
* [Optional: Populate DB with a Demo Sandbox Data Fixture](#demo-sandbox)

<a name="step1"></a>
### Step 1: Get the code

    git clone https://github.com/alariva/timegrid.git

    cd timegrid

-----
<a name="step2"></a>
### Step 2: Install dependencies with Composer

    composer install

-----
<a name="step3"></a>
### Step 3: Create the Database

Once you finished the first three steps, you can create the *MySQL* database server. You must create the database with `utf-8` collation (`utf8_general_ci`), for the application to work.

-----
<a name="step4"></a>
### Step 4: Configure the Environment

**Copy** the **.env.example** file to **.env**

    cp .env.example .env

**Edit** the `.env` file and set the database configuration among the other settings.

Set the application key

    php artisan key:generate

**Edit** all the Primary section parameters (for *local/test/development environment*)

**Change** the storage path in **.env** file to a writeable location

    STORAGE_PATH=/home/username/timegrid/storage

For **local** environment you will need to **comment out** APP_DOMAIN, to keep it *null*

    #APP_DOMAIN=

Back to your console, **migrate** database schema

    php artisan migrate

**Populate** the database:

    php artisan db:seed
    
**Update** [geoip](https://github.com/Torann/laravel-geoip) database:

    php artisan geoip:update

And we are ready to go. **Run** the server:

    php artisan serve

**Type** on web browser:

    http://localhost:8000/

-----
<a name="step5"></a>
### Step 5: Start Page

Congrats! You can now register as new user and log-in.

![timegrid Login Screen](http://i.imgur.com/jM8pbGq.png)

<a name="demo-sandbox"></a>
## Demo Sandbox Fixture

If you want to try the application with a *Lorem Ipsum* database fixture.

    php artisan db:seed --class=TestingDatabaseSeeder

Now you have two demo credentials to log in and play around.

    USER: demo@timegrid.io
    PASS: demomanager

    USER: guest@example.org
    PASS: demoguest

<a name="post-install-steps"></a>
## Post-installation steps

There are some things you may need to set up after the installation is complete.

<a name="crontab-setup"></a>
### Setting up the scheduler

For *scheduled tasks* to operate correctly, you should add the following Cron entry to your server. Editing the crontab is commonly performed with the command `crontab -e`.

    * * * * * php /path/to/artisan schedule:run >> /dev/null 2>&1

Be sure to replace **/path/to/artisan** with the absolute path to the *artisan* file in the root directory of timegrid. This Cron will call the command scheduler every minute.

> **Note**: If you are adding this to `/etc/cron.d` you'll need to specify a user immediately after `* * * * *`.
