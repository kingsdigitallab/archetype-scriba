# archetype-scriba
Archetype-based site for Scriba project

# Pre requisites

* linux environment (ubuntu/debian)
* postgresql 9+
* conda
* git

# SCRIBA DEPLOYMENT LCL

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
conda create -n exon python=2.7 
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

## local_settings.py
```# TODO```

## create db tables
`. activate scriba`
`./manage.py migrate`

# run server
`./manage.py runserver`

# browse your site

open browser as http://localhost:8000/
