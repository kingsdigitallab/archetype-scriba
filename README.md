# archetype-scriba
Archetype-based site for Scriba project

# Pre requisites

* linux environment (ubuntu/debian)
* postgresql 9+
* conda OR python 2.7 (with pip and virtualenv)
* git

# Local deployment

## pull code

```
git clone git@github.com:kcl-ddh/digipal.git digipal_github # TODO: develop branch
git clone git@github.com:kingsdigitallab/archetype-scriba.git
```

## set up project

```
cd archetype-scriba
ln -s ../digipal_github/digipal
ln -s ../digipal_github/digipal_text
ln -s ../digipal_github/build
```

## virtual env
```
conda create -n scriba python=2.7 
. activate scriba
pip install --upgrade --ignore-installed pip
pip install -r build/requirements.txt
```

## database
```
sudo su postgres
psql
create user app_scriba with password 'XXX';
\q
createdb -E 'utf-8' -T template0 -O app_scriba app_scriba_lcl
```

## settings

local_settings.py SHOULD NOT be part of github repo, it is reserved for any sensitive information like database connections, address to image server, etc. and for anything specific to a particular instance of your site.

settings_sriba.py contains your project customisations, anything which is not sensitive and is shared between all instances (local, development, staging, live) of the projects.

## create db tables
`. activate scriba`
`./manage.py migrate`

# run server
`./manage.py runserver`

# browse your site

open browser as http://localhost:8000/
