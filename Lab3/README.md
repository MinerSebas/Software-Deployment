# Lab 3

## Teil 1

Aufgabe: Erstellen eines `docker-compose.yml` datei, die `Wordpress` und `MySQL` images verwendet.

Ausführen der `docker-compose.yml` datei:

```sh
cd ./Teil1
docker compose up -d
```

Nun kann man Wordpress über `localhost:80` erreichen.

Entfernen der erstellten Container:

```sh
cd ./Teil1
# Man kann --volumes verwenden um die persistenz Volumen ebenfalls zu löschen.
docker compose down
```

## Teil 2

Aufgabe: Erstellen eines `docker-compose.yml` datei, die selbst erstellte `Apache + PHP + Wordpress` und `MySQL` images verwendet.

```sh
cd ./Teil2
docker compose up -d
```

Nun kann man Wordpress über `localhost:8080` erreichen.

Entfernen der erstellten Container:

```sh
cd ./Teil1
# Man kann --volumes verwenden um die persistenz Volumen ebenfalls zu löschen.
docker compose down
```
