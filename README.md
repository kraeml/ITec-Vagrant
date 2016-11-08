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

  Alternativ: user: example_user password: Secure-CaHrdf

- <http://192.168.6.10:8888> zu jupyter-lab

- <http://192.168.6.10:8888/tree> jupyter-notebook

- <http://192.168.6.10:8181> Cloud9 Ide

- <http://192.168.6.10:1880> Node-Red
- <http://192.168.6.10:3000> Port wird für Übungen zu nodejs verwendet.

## Start ITec

```bash
cd ~/projekte
if [ -d ITec-Ruby ]
then
    cd ITec-Ruby
    git pull origin master
    git checkout Schuljahr16/17
    git merge origin/master
else
    git clone https://github.com/kraeml/ITec-Ruby.git
    cd ITec-Ruby
    git checkout -b Schuljahr16/17
fi
```

```
Von https://github.com/kraeml/ITec-Ruby
 * branch            master     -> FETCH_HEAD
Already up-to-date.
Bereits auf 'Schuljahr16/17'
Ihr Branch ist auf dem selben Stand wie 'origin/Schuljahr16/17'.
Already up-to-date.
```

```bash
git branch
```

```
* Schuljahr16/17
  master
```

## Ruby und mongodb

Weblinks:

- <https://docs.mongodb.com/getting-started/shell/import-data/>

```bash
wget https://raw.githubusercontent.com/mongodb/docs-assets/primer-dataset/primer-dataset.json -O primer-dataset.json
```

```
--2016-10-05 08:50:30--  https://raw.githubusercontent.com/mongodb/docs-assets/primer-dataset/primer-dataset.json
Auflösen des Hostnamen »raw.githubusercontent.com (raw.githubusercontent.com)«... 151.101.12.133
Verbindungsaufbau zu raw.githubusercontent.com (raw.githubusercontent.com)|151.101.12.133|:443... verbunden.
HTTP-Anforderung gesendet, warte auf Antwort... 200 OK
Länge: 11880944 (11M) [text/plain]
In »»primer-dataset.json«« speichern.

primer-dataset.json 100%[===================>]  11,33M   756KB/s    in 22s     

2016-10-05 08:50:52 (535 KB/s) - »primer-dataset.json« gespeichert [11880944/11880944]
```

```bash
mongoimport --db test --collection restaurants --drop --file ./primer-dataset.json
```

```
2016-10-04T20:44:23.173+0200    connected to: localhost
2016-10-04T20:44:23.178+0200    dropping: test.restaurants
2016-10-04T20:44:26.201+0200    [#######.................] test.restaurants    3.61MB/11.3MB (31.9%)
2016-10-04T20:44:29.162+0200    [################........] test.restaurants    7.80MB/11.3MB (68.8%)
2016-10-04T20:44:32.164+0200    [#######################.] test.restaurants    11.3MB/11.3MB (99.7%)
2016-10-04T20:44:32.205+0200    [########################] test.restaurants    11.3MB/11.3MB (100.0%)
2016-10-04T20:44:32.206+0200    imported 25359 documents
```

### Mongo Shell

Weblinks:

- <https://docs.mongodb.com/getting-started/shell/client/>

In einem Terminal ausführen.

### Mongo Ruby

Weblinks:

- <https://docs.mongodb.com/ruby-driver/master/installation/#ruby-driver-install>
- <https://docs.mongodb.com/ruby-driver/master/quick-start/>

Erst ruby Pakete installieren (s.u.) danach in einem Ruby Notebook durcharbeiten.

```bash
gem install mongo

Successfully installed mongo-2.3.0
Parsing documentation for mongo-2.3.0
Installing ri documentation for mongo-2.3.0
Done installing documentation for mongo after 17 seconds
1 gem installed
```

### Flask

Was ist Flask: <https://de.wikipedia.org/wiki/Flask>

Projekt Seite: <http://flask.pocoo.org/>

Bitte dort die PDF herunter laden. <http://flask.pocoo.org/docs/0.11/.latex/Flask.pdf>

Oder die Dokumentation lesen: <http://flask.pocoo.org/docs/0.11/>

Für Mongodb gibt es hier eine Anleitung: <http://flask.pocoo.org/docs/0.11/patterns/mongokit/>

Funktioniert nicht mit jupyter. Daher mit eigener IDE oder mit [Cloud9][08accaf0] arbeiten.

[08accaf0]: http://192.168.6.10:8181 "Cloud9 IDE"
