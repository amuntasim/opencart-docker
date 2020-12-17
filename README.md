# OpenCart Docker

This repository should make it super simple to run [Opencart](http://www.opencart.com/) in docker containers.

## Installation
1. Firstly, create a project folder and place the OpenCart files insde there.
2. Add the opencart-docker files:
  - if you are using Git already you could add it as a submodule:
      
          $ git submodule add https://github.com/amuntasim/opencart-docker.git
  - if not, either copy the files or clone into the project directory:

          $ git clone https://github.com/amuntasim/opencart-docker.git
3. It should look a bit like this:

        |-- project-root
        |   |-- opencart-docker
        |   |-- tests
        |   |-- upload
        |   |-- vendor
        |   |-- build.xml
        |   |-- changelog.md
        |   |-- etc...

4. Copy the .env-example to .env and make any changes to the environment variables that you want.

        $ cp .env-example .env
        2> copy modificcation.xml to /upload/system
        3> copy cloudsql-credentials.json into opencart-docker
        
5. Now, in the opencart-docker folder, we want run it and serve Opencart. The simplest way is:
        
     $ docker-compose build   
     $ docker-compose up -d 
        
6. Finally we need to be able to access the site. We need to put the docker ip address into the HOSTS file.
This will be different on different operating systems.
  ### Linux
  1. Simple. Docker is native so open `/etc/hosts` and add
  
          127.0.0.1 opencart.test
  
  
  ### Windows
  1. Firstly, make sure the docker-machine is up and running and type the command `docker-machine ip`
  2. Copy this value, usually `192.168.99.100`
  3. Add this to your HOSTS file (usually) `C:/Windows/System32/drivers/etc/hosts`
  
          192.168.99.100 opencart.test

7. Visit http://opencart.test/ :-)

8. The OpenCart install is now really simple. 
  1. Create the `config.php` files in both `upload/` and `upload/admin/`.
  2. In the database configuration use the values in `.env`.
  The defaults are:
      - **hostname**: mysql
      - **username**: opencart
      - **password**: password
      - **database**: opencart
  3. Click continue and then OpenCart should install and you should be able to access your store! 
