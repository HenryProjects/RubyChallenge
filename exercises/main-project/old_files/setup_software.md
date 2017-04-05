Previous step: [Main Project](readme.md)  
Next step: [Setup Heroku](setup_heroku.md)

# Software Setup

1. Download and/or Install Required Software
2. Get the project on your machine
3. Test that the app runs on your local machine

## Download and/or Install Required Software
Follow the links for instructions on installing the required software: 

* [Ruby](prereqs/setup_ruby.md)
* [PostgresSQL.app](prereqs/setup_postgres.md)
* [Bundle Install](prereqs/setup_bundle_install.md)
* [Github Enterprise Account](https://newrelic.atlassian.net/wiki/display/eng/Git+Setup+for+New+Employees)
* [Personal New Relic Account](prereqs/setup_personal_nr.md)
* [Text Editor](prereqs/setup_text_editor.md)


## Get the project on your machine
*NOTE: For detailed instructions on forking and cloning, see [GitHub Help] (https://help.github.com/enterprise/2.4/user/articles/fork-a-repo/)*
* Fork the project from here (https://source.datanerd.us/motis/newrelic-ruby-kata-newb-relic) to your personal github directory
* Clone the fork to your machine
* Run Bundle Install - Installs the gems you need to run the application
 * Terminal cd [location for root directory for the project] for example: 
   ```
   $ cd ~/code/newrelic-ruby-kata-newb-relic
   ```
 * Then install the gems
   ```
   $ bundle install
   ```

## Test that the app runs on your local machine

* Create a database  
  ```
  $ rake db:create
  ```
* Populate the database with data  
  ```
  $ pg_restore --verbose --clean --no-acl --no-owner -h localhost -U $USER -d newrelic-ruby-kata_development public/sample-data.dump
  ```  
This restores a PostgreSQL database from the archive file: sample-data.dump
* Test to make sure the newrelic-ruby-kata works on your local machine by typing:   
  ```
  $ rails server
  ```  
![rails server](images/terminal-rails-server.png)  
If it looks like this, you’re good.

If not, it might mean you need to install/reinstall rails on your machine in this directory. Once rails finishes installing/reinstalling close and reopen your terminal to reset any environmental variables.

## Test the Application Locally

* Test it by going to your browser and typing: localhost:3000
 * If the page loads you’re most of the way there.
 * Select **Kata Pages > The Loop**  
 if this loads then yes the database was setup correctly locally and you’re good to deploy.
* Close your browser window, and turn off the rails server in Terminal by pressing **Ctrl-C** to quit the rails server

## Congrats!

Your machine is now setup properly. You've got all the code you need. And you are ready to deploy the web app. 

Next step: [Setup Heroku](setup_heroku.md)

