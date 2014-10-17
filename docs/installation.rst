
Installation
------------
Installation should be quick and straightforwad. 

Debian packages
'''''''''''''''

::

    sudo apt-get install virtualenv python-dev
    sudo apt-get install libmysqlclient-dev mysql-server
    sudo apt-get g++

Mac setup
'''''''''''''''

::

    # Install mysql
    brew install mysql
    # Start mysql
    mysql.server start

    # Install python package managers
    sudo easy_install pip
    sudo pip install virtualenv
    

Required environment variable, add this to your .bashrc or .bash_profile
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

::

    export AIRFLOW_HOME=~/Airflow
    export PATH=$PATH:$AIRFLOW_HOME/airflow/bin
    # also run it, or source it, or start a new shell
    source ~/.bashrc

Create a python virtualenv
''''''''''''''''''''''''''

::

    virtualenv env # creates the environment
    source init.sh # activates the environment

Use pip to install the python packages required by Airflow
''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

::

    pip install -r requirements.txt

Setup the metdata database
''''''''''''''''''''''''''

Here are steps to get started using MySQL as a backend for the metadata
database, though any backend supported by SqlAlquemy should work just
fine.

::

    $ mysql -u root -p 
    mysql> 
    CREATE DATABASE airflow;
    CREATE USER 'airflow'@'localhost' IDENTIFIED BY 'airflow';
    GRANT ALL PRIVILEGES ON airflow.* TO 'airflow'@'localhost';

Get things started
''''''''''''''''''''

::

    # Creating the necessary tables in the database
    airflow initdb

    # Start the web server!
    airflow webserver --port 8080