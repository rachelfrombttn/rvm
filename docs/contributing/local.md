# Running RVM in local development environment

To test a local copy of RVM for development purposes simply enter the folder with the source and install it:
 
```
./install && rvm reload
```

If you don't want to destroy your working environment, you can select a different destination folder and easily switch between them:

```
./install --path ~/.rvm-dev
rvm switch ~/.rvm-dev           # development version
rvm switch ~/.rvm               # production version
```
