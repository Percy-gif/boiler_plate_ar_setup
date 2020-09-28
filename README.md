# Mod 1 ActiveRecord Starter Repo

In `config/database.yml`, you can change the name of the database from `db/cats.sqlite3` to whatever reflects your project. For example: `db/notes.sqlite3`. Doesn't really matter what you call the db. 



## ActiveRecord Methods
These common ActiveRecord methods will help you interact with your database. Please refer to the ActiveRecord
docs for what they do and how to use them. (If the docs talk about Rails, that is ok! ActiveRecord works very
 similar with or without Rails.)
```
  .create (.new, .save)
  .all
  .count
  .find
  .find_by
  .where
```

#### Notes

*Remember*, any model that will have a corresponding table in the database needs to inherit from `ActiveRecord::Base`
ex:
```
class Cat < ActiveRecord::Base
  # customer methods defined here
end
```

- To view database, you can run `sqlite3 db/cats.db`, then can run `.schema` or `.tables` and can run any SQL commands. (Don't need to do this anymore though! ActiveRecord gives us a schema file!)


### Steps to setup Ruby app with activerecord
(New for ActiveRecord 6.0)


## The following steps are already done for you in this boiler plate repo. 
## The steps below are provided to you as a reference only. 
## You're not expected to memorize this (please don't).


1. In root of project, run `bundle init`
1. Add gems: 
  `bundle add activerecord pry sinatra, sinatra-activerecord rake sqlite3 require_all`
  run `bundle install`
1. mkdir config and lib 
1. mkdir lib/models
1. touch config/environment.rb config/database.yml
1. Create your model files and models (make sure to have your models inherit from ActiveRecord::Base)
1. In config/environment.rb:
```
  require 'bundler/setup'
  Bundler.require

  require_all 'lib'
```
1. In config/database.yml:
  ```
  development:
    adapter: sqlite3
    database: db/cats.sqlite3
  ```
1. Touch Rakefile - require ‘config/environment.rb’ and require_relative ‘sinatra/activerecord/rake’ 
1. Run rake -T to make sure we have access to raketasks
1. Run `rake db:create_migration NAME=create_cats_table` (will create the db folder if it doesn’t already exist) and will add the migration file to db/migration
1. Write migration file, then run `rake db:migrate`
1. Then can see schema in file structure, can also drop into sqlite3 cats.db to see the tables and schema, but don’t really need to do that anymore. *Review rollback here*
1. Create seeds in db/seeds.rb and run `rake db:seed`
1. Now can put a pry in environment.rb to run <ModelName>.all and see your seeds.

Make sure your models inherit from `ActiveRecord::Base`

#######notes 
at first, considered the following 
1. config 
2. database 
  adapter -= what kind of database we're using 
3. mkdir lib - creates a library folder, which is required in the environment file 
3.a. mkdir lib/models folder to hold our database models here 
3.b. touch lib/models/beverage.rb --> creates a file for us to store our beverage class 
4. rakefile - brings in our environment file 
5. run rake -T (shows us all our commands); the 3 most imp are 
   a. create migrations
   b. migrate 
   c. seed
   * this is a great test for seeing if everything works. if it does, you can run your commands 
6. rake db:create_migration NAME=create_beverages_table 
6b.rake db:create_migration NAME=create_alcohols_table 
   -- creates migration tables 

  Schema - just a rep of your database 

#####most imp files 
1. database
2. environment 
3. rake 

(1)NOTE - classes should be singular 

(2)- subclasses 
class Beverage < ActiveRecord::Base #base is "sub" to the AR module 
(3) errors - AR errors are gen at the top. go gthere first 
(4) symbol vs. key:value pair -- refers to notation used in AR (inc)
(5) binding.pry - 

    
end

# :: subclass 
--------
migrations 
seeds/seeding
creating relationsships 
## these 3 concepts will be the focus for the rest of the course 