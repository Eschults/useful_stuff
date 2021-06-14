# useful_stuff
Memo for my beloved students

## Summary

- [Keyboard's shortcuts (Mac)](#keyboards-shortcuts-mac)
  - [Special characters](#special-characters)
  - [Navigate](#navigate)
  - [Text Editor](#sublime-text)
  - [Terminal](#terminal)
  - [Chrome](#chrome)
- [Keyboard's shortcuts (LINUX)](#keyboards-shortcuts-linux)
  - [Text Editor](#sublime-text-1)
  - [Terminal](#terminal-1)
- [Frequently misunderstood error messages](#frequently-misunderstood-error-messages)
  - [NoMethodError: undefined method `some_method' for some_object:SomeType](#nomethoderror-undefined-method-some_method-for-some_objectsometype)
  - [TypeError: SomeType can't be coerced into SomeOtherType](#typeerror-sometype-cant-be-coerced-into-someothertype)
  - [TypeError: no implicit conversion of SomeType into SomeOtherType](#typeerror-no-implicit-conversion-of-sometype-into-someothertype)
  - [ArgumentError: wrong number of arguments (given N, expected M)](#argumenterror-wrong-number-of-arguments-given-n-expected-m)
  - [PG::Error FATAL "myapp_development" does not exist](#pgerror-fatal-myapp_development-does-not-exist)
  - [ActiveRecord::PendingMigrationError Migrations are pending](#activerecordpendingmigrationerror-migrations-are-pending)
  - [PG::ConnectionBad - could not connect to server: No such file or directory](#pgconnectionbad---could-not-connect-to-server-no-such-file-or-directory-is-the-server-running-locally-and-accepting-connections-on-unix-domain-socket-tmpspgsql5432)
  - [NameError: uninitialized constant ClassName](#nameerror-uninitialized-constant-classname)
  - [ResourcesController#action is missing a template for this request format and variant.](#resourcescontrolleraction-is-missing-a-template-for-this-request-format-and-variant)
  - [Pundit::NotDefinedError in SomeController#some_action](#punditnotdefinederror-in-somecontrollersome_action)
  - [Pundit::AuthorizationNotPerformedError in SomeController#some_action](#punditauthorizationnotperformederror-in-somecontrollersome_action)
  - [Pundit::NotAuthorizedError in SomeController#some_action](#punditnotauthorizedderror-in-somecontrollersome_action)
- [Mastering git](#mastering-git)
  - [Starting a new feature](#starting-a-new-feature)
  - [Finishing a feature](#finishing-a-feature)
  - [Getting latest changes from master](#getting-latest-changes-from-master)
  - [Conflicts solving](#conflicts-solving)
  - [Accidental commit to master](#fix-an-accidental-commit-to-master)
- [Useful gems](#useful-gems)
- [Going further](#going-further)

## Keyboard's shortcuts (Mac)
### Special characters
```ruby
{ # alt + (
} # alt + )
[ # alt + shift + (
] # alt + shift + )
| # alt + shift + l
~ # alt + n
\ # alt + /
```

### Navigate
```ruby
from one program to another                # cmd + tab
from one window to another (same program)  # cmd + `
```

### Text Editor (Sublime Text or VS Code with Sublime Text Keymap)
```ruby
open a file in current project             # cmd + p (or cmd + t)
paste with indentation                     # cmd + shift + v
move a line upwards in file                # ctrl + cmd + ↑
move a line downwards in file              # ctrl + cmd + ↓
(un)comment lines                          # cmd + /
search in file                             # cmd + f
search in project                          # cmd + shift + f
add package                                # cmd + shift + p
add indentation                            # tab
remove indentation                         # shift + tab
reach next word                            # alt + →
reach previous word                        # alt + ←
reach end of line                          # cmd + →
reach beginning of line                    # cmd + ←
close tab                                  # cmd + w
reopen last tab closed                     # cmd + shift + t
navigate to tab on the right               # cmd + alt + →
navigate to tab on the left                # cmd + alt + ←
duplicate line                             # cmd + shift + d
remove line                                # ctrl + shift + k
split view into two columns                # cmd + option + 2
split view into two rows                   # cmd + option + shift + 2
```

### Terminal
```ruby
open a new tab                             # cmd + t
close tab                                  # cmd + w
clear window (keeping history)             # ctrl + l
clear window (losing history)              # cmd + k
reach next word                            # alt + →
reach previous word                        # alt + ←
reach beginning of line                    # ctrl + a
reach end of line                          # ctrl + e
erase the whole line                       # ctrl + u
navigate to tab on the right               # cmd + shift + →
navigate to tab on the left                # cmd + shift + ←
```

### Chrome
```ruby
open developer tools (elements)            # cmd + alt + i
open developer tools (console)             # cmd + alt + j
change docking location                    # cmd + shift + d

navigate to tab on the right               # cmd + alt + →
navigate to tab on the left                # cmd + alt + ←
open a new tab                             # cmd + t
focus on address bar                       # cmd + l
close tab                                  # cmd + w
reopen last tab closed                     # cmd + shift + t

hard refresh (clear cache)                 # cmd + shift + r
```

## Keyboard's shortcuts (LINUX)

### Text Editor (Sublime Text or VS Code with Sublime Text Keymap)
```ruby
open a file in current project             # ctrl + p
paste with indentation                     # ctrl + shift + v
move a line upwards in file                # ctrl + shift + ↑
move a line downwards in file              # ctrl + shift + ↓
(un)comment lines                          # ctrl + shift + :
search in file                             # ctrl + f
search in project                          # ctrl + shift + f
add package                                # ctrl + shift + p
add indentation                            # tab
remove indentation                         # shift + tab
move text cursor to next word              # alt + →
move text cursor to previous word          # alt + ←
close tab                                  # ctrl + w
reopen last tab closed                     # ctrl + shift + t
duplicate line                             # ctrl + shift + d
```

### Terminal
```ruby
open a new tab                             # ctrl + shift + t
close tab                                  # ctrl + shift + w
clear window                               # ctrl + L (or type "clear" in terminal)
```

## Common error messages
The first advice I'll throw here is to **read patiently, entirely, twice** the error message when one occurs.
This can get tricky when you read it from a tiny terminal window, so start by opening it wide to have a clear look at its face.

### Ruby

#### ``NoMethodError: undefined method `some_method' for some_object:SomeType``

```ruby
# It means that `some_object` **on which you call** `.some_method` is not of the right type.
# You'll get this error if you try to call a `String` instance method on a `Fixnum` for example.
# Its most frequent expression is when `some_object` is nil:

recipe.name
# => NoMethodError: undefined method `name' for nil:NilClass
# `recipe` is nil, it shouldn't!
```

#### `TypeError: SomeType can't be coerced into SomeOtherType`

```ruby
# It means that you're trying to mix apples and oranges.

1 + nil
# => TypeError: nil can't be coerced into Fixnum

2 + "2"
# => TypeError: String can't be coerced into Fixnum
```

#### `TypeError: no implicit conversion of SomeType into SomeOtherType`

```ruby
# Its cousin.

"2" + 2
# => TypeError: no implicit conversion of Fixnum into String
```

#### `ArgumentError: wrong number of arguments (given N, expected M)`

```ruby
# It means that you're calling a method that takes M parameters with N arguments.
# Either your definition of that method is wrong, either you're calling it with the wrong number of arguments.

def full_name(first_name, last_name)
  return first_name.capitalize + " " + last_name.capitalize
end

full_name("boris")
# => ArgumentError: wrong number of arguments (given 1, expected 2)
```

### Rails

#### `PG::Error FATAL "myapp_development" does not exist`

```ruby
# Just run `rails db:create` in your terminal.
```

#### `ActiveRecord::PendingMigrationError Migrations are pending`
```ruby
# Just run `rails db:migrate` in your terminal.
```

#### `PG::ConnectionBad - could not connect to server: No such file or directory Is the server running locally and accepting connections on Unix domain socket "/tmp/.s.PGSQL.5432"?`

```bash
# It means that PG did not exit gracefully last time your computer was shut off.
# Run the following in your terminal:

rm /usr/local/var/postgres/postmaster.pid
```

#### `NameError: uninitialized constant ClassName`

```ruby
# In most cases, you'll get this error message when you're implementing a gem
# and you forgot to restart your `rails server` after running `bundle install`.
```

#### `ResourcesController#action is missing a template for this request format and variant.`

```ruby
# After executing the code in a controller's action, Rails conventionnally
# renders the template named `action.html.erb` in `app/views/resources`.
# It thus means you forgot to generate action's associated view, that you
# misspelled its filename, or that you misplaced it.
```

#### `Pundit::NotDefinedError in SomeController#some_action`

```bash
# The policy is not defined for this controller!
rails g pundit:policy **name_of_the_resource_in_singular**
```

#### `Pundit::AuthorizationNotPerformedError in SomeController#some_action`

```ruby
# You need to call `authorize(@some_resource)` in the action (in the controller)
# Make sure you insert this line before saving the resource in your DB!
```

#### `Pundit::NotAuthorizedError in SomeController#some_action`

```ruby
# The rule returns false, you should override ApplicationPolicy's rule by setting it in corresponding ResourcePolicy
# Don't forget to rescue this error with a flash and a redirection at ApplicationController's level!
```

## Mastering git

### Starting a new feature

When you want to start a new feature.
You have to create a new branch to work from:

```
(master) git status (CLEAN)
(master) git checkout -b my-feature
```

### Finishing a feature

You've just finished you feature.
Now it's time to make a last commit, create a pull request and go back to master branch:

```
(my-feature) git add .
(my-feature) git commit -m 'XXXX'
(my-feature) git push origin my-feature

(my-feature) git status (CLEAN)

(my-feature) gh repo view --web
[GO CREATE A PULL REQUEST ON GITHUB]

(my-feature) git checkout master
(master)     git pull origin master
(master)     git sweep

(master)     git checkout -b my-new-feature
```

### Getting latest changes from master

When you want to get the latest changes from master on my branch:

```
(my-feature) git add .
(my-feature) git commit -m 'XXXX'

(my-feature) git status (CLEAN)

(my-feature) git checkout master
(master)     git pull origin master

(master)     git checkout my-feature
(my-feature) git merge master
```

### Conflicts solving

When you can't merge a PR due to conflicts in an `unmergeable_branch`, follow this process:

```ruby
# first make sure your git status is clean on your current branch
git status # if not clean, add and commit your work

# go to your local master branch
git checkout master

# update your master branch locally with github's master
git pull origin master

# go back to unmergeable_branch
git checkout unmergeable_branch

# merger master in unmergeable branch to solve conflicts locally
git merge master

# now you've fetched all conflicts locally, time to solve them
# open sublime and solve conflicts (locate them with cmd + shift + f <<<<<<<)

# commit your code
git add .
git commit -m "conflict solving"
git push origin unmergeable_branch

# open your PR on github to merge it
hub browse

# merge your PR on github

# go back to your terminal and update your local master with merged files
git checkout master
git pull origin master

# create a new branch for next feature
git checkout -b next_feature
```

### Fix an accidental commit to master

When you committed some changes to `master` and wanted to commit them to a new branch, follow this process:

```ruby
# create a new branch from the current state of master
git checkout -b some-new-branch-name

# remove the commit from the master branch
git checkout master
git reset HEAD~ --hard

# go back to your new branch
git checkout some-new-branch-name
# your commit lives in this branch now

# if you want to make sure it does...
git push origin some-new-branch-name

# ...go check it out by yourself
hub browse
```

## Useful gems

#### [Acts as votable](https://github.com/ryanto/acts_as_votable)
Perfect for like / upvote / save to wishlist features!
#### [Public Activity](https://github.com/chaps-io/public_activity)
A good framework to handle notifications.
Check [this railscast](http://railscasts.com/episodes/406-public-activity) out to set it up in your project!

## Going further

#### [10 common mistakes using Rails](https://www.toptal.com/ruby-on-rails/top-10-mistakes-that-rails-programmers-make)
#### [The Vital Guide to Ruby on Rails Interviewing](https://www.toptal.com/ruby-on-rails#skill_article_content_title)
