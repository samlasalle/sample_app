# Ruby on Rails Tutorial
This is the sample application for
[*Ruby on Rails Tutorial:
Learn Web Development with Rails*](http://www.railstutorial.org/)
by [Michael Hartl](http://www.michaelhartl.com/).
## License
All source code in the [Ruby on Rails Tutorial](http://railstutorial.org/)
is available jointly under the MIT License and the Beerware License. See
[LICENSE.md](LICENSE.md) for details.
## Getting started
To get started with the app, clone the repo and then install the needed gems:
```
$ bundle install --without production
```
Next, migrate the database:
```
$ rails db:migrate
```
Finally, run the test suite to verify that everything is working correctly:
```
$ rails test
```
If the test suite passes, you'll be ready to run the app in a local server:
```
$ rails server
```

## CH 1 From zero to deploy

default rails project structure:
app/          core code (incl. models, views, controllers, helpers)
app/assets    assets such as CSS, JavaScript, image
bin/          binary executable files
config/       app config
db/           db files
doc/          documentation
lib/          library modules
lib/assets    library assets e.g. CSS, JavaScript, images
log/          logs
public/       public
bin/rails     rails exec
test/         tests
tmp/          tmp
vendor/       third party code: plugins, gems
vendor/assets third party assets e.g. CSS, JavaScripts, images
README.md     readme
Rakefile      utility tasks used with 'rake'
Gemfile       packages required
Gemfile.lock
config.ru     config for Rack middleware

still to do: think about deployment. heroku is one good option.

## CH 2 A toy app

- scaffold generators are good
rails _5.1.4_ new toy_app

- set root route with "root 'controller#action'" in config/routes.rb

rails generate scaffold User name:string email:string
rails db:migrate
- model names are singular e.g. 'User'
- resources and controllers are plural e.g. 'Users'
- automatically creates CRUD routes!!

"A visit to /users" in MVC:
1. browser requests /users URL
2. rails routes /users to index action in Users controller
3. index action requests all users from User model
4. User model pulls all users from DB
5. User model returns list of users to controller
6. controller stores list in @users variable, passes to index view
7. view uses embedded Ruby to render page as HTML
8. controller passes HTML to browser

- controllers contain sets of actions
  @users = User.all = steps 3, 4, 5

"A visit to /users/1/edit" in MVC:
1. browser requests /users/1/edit URL
2. rails routes /users/1/edit to edit action in Users controller
3. edit action requests user with id = 1 from User model
4. User model gets user with id = 1 from DB
5. User model returns the user object to the controller
6. Controller saves user in @user variable, which is passed to eidt view
7. view uses embedded Ruby to render as HTML
8. controller passes HTML to browser

  @user = User.find(params[:id])

Weaknesses with scaffolding:
- no data validation
- no auth
- no tests for custom reqs
- no style or layout
- no real understanding

- REST = REpresentational State Transfer
  - in ruby, apply CRUD ops to resources

## Further reading:
- 'learn enough to be dangerous' tutorials
- tutorials.railsapps.org - topic-specific rails projects/tutorials
