# reproducer

## Description

It seems to be that flex 1.3 and 1.4 are causing a scan of all branches of my fork of `bernard` on install.
This is very slow. It does not happen on flex 1.2.7.

```shell script
git clone git@github.com:bendavies/flex-scanning-branches.git
cd flex-scanning-branches
git checkout master

# master branch is flex 1.2.7 which seems fine
rm -rf vendor && composer clear && composer i

git checkout 1.3.1
rm -rf vendor && composer clear && composer i
#notice that all branches are scanned

git checkout 1.4.0
rm -rf vendor && composer clear && composer i
#notice that all branches are scanned

git checkout master
rm -rf vendor && composer clear && composer i
#all fine
```