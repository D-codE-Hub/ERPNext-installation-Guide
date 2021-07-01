# ERPNext-installation-Guide
# The complete guide to install ERPNext in your Ubuntu system

# Pre-requisites 

      Python 3.6+
      Node.js 12
      Redis 5                                       (caching and real time updates)
      MariaDB 10.3.x / Postgres 9.5.x               (to run database driven apps)
      yarn 1.12+                                    (js dependency manager)
      pip 20+                                       (py dependency manager)
      wkhtmltopdf (version 0.12.5 with patched qt)  (for pdf generation)
      cron                                          (bench's scheduled jobs: automated certificate renewal, scheduled backups)
      NGINX                                         (proxying multitenant sites in production)



# STEP 1 Install git
Git is the most commonly used version control system. Git tracks the changes you make to files, 
so you have a record of what has been done, and you can revert to specific versions should you ever need to. 
Git also makes collaboration easier, allowing changes by multiple people to all be merged into one source.
    
    sudo apt-get install git

# STEP 2 install python-dev
python-dev is the package that contains the header files for the Python C API, 
which is used by lxml because it includes Python C extensions for high performance.

    sudo apt-get install python3-dev

# STEP 3 Install setuptools and pip (Python's Package Manager).
Setuptools is a collection of enhancements to the Python distutils that allow developers 
to more easily build and distribute Python packages, especially ones that have 
dependencies on other packages. Packages built and distributed using setuptools 
look to the user like ordinary Python packages based on the distutils.

pip is a package manager for Python.  It's a tool that allows you to install and manage 
additional libraries and dependencies that are not distributed as part of the standard library.

    sudo apt-get install python3-setuptools python3-pip

# STEP 4 Install virtualenv
virtualenv is a tool for creating isolated Python environments containing their own copy of
python , pip , and their own place to keep libraries installed from PyPI.
It's designed to allow you to work on multiple projects with different dependencies 
at the same time on the same machine.
    
    sudo apt-get install virtualenv

# STEP 5 Install MariaDB 10.3 stable package
MariaDB is developed as open source software and as a relational database it provides an SQL interface 
for accessing data.

open this link

    https://downloads.mariadb.org/mariadb/repositories/#mirror=piconets

IMPORTANT :During this installation you'll be prompted to set the MySQL root password.
If you are not prompted for the same You can initialize the MySQL server setup by executing 
the following command
    
    sudo mysql_secure_installation
    
# STEP 6  MySQL database development files

    sudo apt-get install libmysqlclient-dev

# STEP 7 Edit the mariadb configuration ( unicode character encoding )

    sudo nano /etc/mysql/my.cnf

add this to the my.cnf file

    [mysqld]
    character-set-client-handshake = FALSE
    character-set-server = utf8mb4
    collation-server = utf8mb4_unicode_ci

    [mysql]
    default-character-set = utf8mb4

Now press (Ctrl-X) to exit

    sudo service mysql restart

# STEP 8 install Redis
Redis is an open source (BSD licensed), in-memory data structure store, used as a database, 
cache, and message broker.
    
    sudo apt-get install redis-server

# STEP 9 install Node.js 12.X package
Node.js is an open source, cross-platform runtime environment for developing server-side and 
networking applications. Node.js applications are written in JavaScript, and can be run within the Node.js
runtime on OS X, Microsoft Windows, and Linux.

    sudo apt-get install curl
    curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
    sudo apt-get install -y nodejs

# STEP 10  install Yarn
Yarn is a JavaScript package manager that aims to be speedy, deterministic, and secure. 
See how easy it is to drop yarn in where you were using npm before, and get faster, more reliable installs.
Yarn is a package manager for JavaScript.
    
    sudo npm install -g yarn

# STEP 11 install wkhtmltopdf
Wkhtmltopdf is an open source simple and much effective command-line shell utility that enables 
user to convert any given HTML (Web Page) to PDF document or an image (jpg, png, etc)

    wget https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6-1/wkhtmltox_0.12.6-1.bionic_amd64.deb
    sudo apt install ./wkhtmltox_0.12.6-1.bionic_amd64.deb
    rm wkhtmltox_0.12.6-1.bionic_amd64.deb
    

# STEP 12 install frappe-bench

    pip3 install frappe-bench

IMPORTANT: you may wish to log out and log back into your terminal 
before next step and You must login.
    
    bench --version
   


# optional step
# STEP  Create a user

    sudo adduser dcode-frappe
    sudo usermod -aG sudo dcode-frappe
    su - dcode-frappe
    
