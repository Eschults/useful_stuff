# useful_stuff
Memo for my beloved students

### Conflicts solving
When you can't merge a PR due to conflicts in an `unmergeable_branch`, follow this process:

```ruby
# checkout your local master branch
git checkout master

# update your master branch locally with github's master
git pull origin master

# checkout unmergeable_branch
git checkout unmergeable_branch

# merger master in unmergeable branch to solve conflicts locally
git merge master

# now you've fetched all conflicts locally, time to solve them
# open sublime and solve conflicts (locate them with cmd + shift + f <<<<<<<)

# commit your code
git add .
git commit -m "conflict solving"
git push origin unmergeable_branch

# open your PR in github to merge it
hub browse

# merge your PR in github

# go back to your terminal and update your local master with merged files
git checkout master
git pull origin master

# create a new branch for next feature
git checkout -b next_feature
```
