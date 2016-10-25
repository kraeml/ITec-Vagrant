# Projekt ITEC an der RDF

## Erste Schritte

Kopieren oder clonen dieses Projektes.

Zip-file:

- <https://elsis.franken.de:8443/kraeml/itec/repository/archive.zip?ref=master>
- In ein Verzeichnis itec unzippen.
- In das Verzeichnis itec wechseln
- Ggf. `vagrant box update`
- Ggf. `vagrant box destroy`
- `vagrant up`

```bash
git clone https://elsis.franken.de:8443/kraeml/itec.git
cd itec
git checkout -b IhrName
vagrant box update
vagrant up
```

## Neue Version via git einspielen

Sie sind im Verzeichnis itec im Branch IhrName.

```bash
git add .
git commit -am "Stand von HEUTE"
git checkout master
git pull
git checkout IhrName
git merge master
vagrant destroy --force
vagrant box update
vagrant up
```

## URLs von ITec

- <http://192.168.6.10> führt zu pma user root pw "Calvin and Hobs mit einfachen Jahrgang"
- <http://192.168.6.10:8888> zu jupyter-lab
- <http://192.168.6.10:8888/tree> jupyter-notebook
- <http://192.168.6.10:8181> Cloud9 Ide
- <http://192.168.6.10:1880> Node-Red
- <http://192.168.6.10:3000> Port wird für Übungen zu nodejs verwendet.
