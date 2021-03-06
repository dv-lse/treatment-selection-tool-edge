WEIGHTED MEAN DATASET VIEWER
============================


Run test suite in browser
=========================

http-server -c-1
open http://localhost:8080/test/index.html
[ then view console log ]


Edge deploy
===========

git checkout gh-edge
git rebase edge

jspm bundle index.js --inject --minify

git add config.js build.*
git commit --amend --no-edit

git push gh-edge gh-edge:gh-pages --force


Staging deploy
==============

git checkout gh-pages
git rebase master

jspm bundle index.js --inject --minify

git add config.js build.*
git commit --amend --no-edit

git push github gh-pages --force


Move Github Edits on gh-pages back to master
============================================

# cherry pick each new commit in order
git checkout master
git cherry-pick <HASH>   # for each new commit on github/gh-pages
# update the gh-pages branch
git checkout gh-pages
git rebase master
# delete the old cherry-picked commits
git checkout github/gh-pages
git reset --hard gh-pages
