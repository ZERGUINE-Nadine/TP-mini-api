# TP — Conteneuriser une mini API 

## Structure du projet
```
mini-api/
├── app.py
├── requirements.txt
└── Dockerfile
└── screenshots/
```


## Étape 1 — Construire l'image

```bash
docker build -t mini-api:1.0 .
```
Capture d'écran : 1

---

## Étape 2 — Lancer le conteneur

```bash
docker run -d -p 5000:5000 --name api mini-api:1.0
```
Capture d'écran : 2


```bash
docker rm api
docker run -d -p 5001:5000 --name api mini-api:1.0
```
Capture d'écran : 3



---

## Étape 3 — Vérifier que le conteneur tourne

```bash
docker ps
```





---

## Étape 4 — Tester l'API

```bash
curl http://localhost:5001/health
```
![alt text](/screenshots/1.png)
Capture d'écran : 4


---

## Étape 5 — Consulter les logs

```bash
docker logs api
```
`

Capture d'écran : 5


---

## Étape 6 — Entrer dans le conteneur

```bash
docker exec -it api bash
ls /app
```

Capture d'écran : 6

---

## Étape 7 — Modifier le code et reconstruire


```bash
docker stop api && docker rm api
docker run -d -p 5001:5000 --name api mini-api:1.0
curl http://localhost:5001/health
```

---

## Étape 8 — Nettoyage

```bash
docker stop api && docker rm api
docker rmi mini-api:1.0
```
Capture d'écran : 7



```bash
docker ps -a
docker images
```

Capture d'écran : 8


---

