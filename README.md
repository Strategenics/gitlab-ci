## 1. Setup

    # bundle

    # Login to MySQL
    $ mysql -u root -p

    # Create the GitLab CI database
    mysql> CREATE DATABASE IF NOT EXISTS `gitlab_ci` DEFAULT CHARACTER SET `utf8` COLLATE `utf8_unicode_ci`;


    # Copy config file
    cp config/application.yml.example config/application.yml

    # Setup DB
    bundle exec rake db:migrate


## 2. Run

    # For development 
    bundle exec foreman start -p 5000


    # For production
    bundle exec thin start -p 3000 -d -e production
    PIDFILE=./resque.pid BACKGROUND=yes QUEUE=* bundle exec rake resque:work
    