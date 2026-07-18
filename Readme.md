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
![alt text](/screenshots/1.png)
---

## Étape 2 — Lancer le conteneur

```bash
docker run -d -p 5000:5000 --name api mini-api:1.0
```
Capture d'écran : 2
![alt text](/screenshots/2.png)

```bash
docker rm api
docker run -d -p 5001:5000 --name api mini-api:1.0
```
Capture d'écran : 3
![alt text](/screenshots/3.png)


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
![alt text](/screenshots/4.png)
Capture d'écran : 4
![alt text](/screenshots/4.png)

---

## Étape 5 — Consulter les logs

```bash
docker logs api
```
`

Capture d'écran : 5
![alt text](/screenshots/5.png)

---

## Étape 6 — Entrer dans le conteneur

```bash
docker exec -it api bash
ls /app
```

Capture d'écran : 6
![alt text](/screenshots/6.png)
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
![alt text](/screenshots/7.png)


```bash
docker ps -a
docker images
```

Capture d'écran : 8
![alt text](/screenshots/8.png)

---

